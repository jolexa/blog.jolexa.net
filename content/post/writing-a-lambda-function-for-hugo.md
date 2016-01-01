+++
categories = ["technical"]
date = "2016-01-01T02:36:15Z"
tags = ["hugo", "lambda", "aws", "amazon"]
title = "Writing a Lambda Function for Hugo"
+++

This post will describe how I choose to implement an AWS Lambda function to
build a static website. As I alluded to in the (previous
post)[/post/migrate-to-hugo-from-wordpress/], here are the details.

{{< tweet 681685189194481664 >}}

For those not familar with Lambda, please see https://aws.amazon.com/lambda/ -
the slogan fits, "Run code, not servers" and it is really neat if you can find a
practical application.

My experience writing this function was mixed. Yes, it is awesome that I only
need to do a git push and the function pushes code to website. No, it was not
fun writing the function since debugging this service is not realtime and pretty
painful. Since Hugo is written in Go, I could easily build the site anywhere
without a complicated localhost setup or build environment. However, since the
website is now serverless, I wanted a serverless method to push code as well. It
works, it isn't super pretty but now I don't have to touch it again.

My [implementation](https://github.com/jolexa/hugo-lambda-function) is different
than other's work that I have found. When I searched for some ideas on how to do
this, I found that [most](https://github.com/ryansb/hugo-lambda)
[people](https://www.airpair.com/lambda/posts/aws-lambda-stream-processing) were
[operating](https://cloudacademy.com/amazon-web-services/labs/automated-static-
site-generation-using-aws-s3-and-lambda-24/) on S3
[events](https://discuss.gohugo.io/t/hugo-build-system-on-aws-lambda/1197/6).
This is fine, but it still needed some human/thing to push the raw content into
S3 first. Then I [see](https://www.google.com/webhp?sourceid=chrome-
instant&ion=1&espv=2&ie=UTF-8#newwindow=1&q=wercker+hugo)
[that](http://sa.muel.be/2015/continuous-integration-with-hugo-and-wercker/)
[there](http://ig.nore.me/2015/01/hugo-build-step-for-wercker/) are
[many](https://gohugo.io/tutorials/automated-deployments/) people using
[Wercker](http://wercker.com/) to automate the deployment, but that seems non-
ideal to me when we have the option to use Lambda for
[free](https://aws.amazon.com/lambda/pricing/) as well. I, personally, want to
minimize the amount of services in play.

### Step - by - Step (Simple)
1. Configure your repo to push to AWS SNS Topic - you will have to configure
this topic
  * Github Repo Settings -> Webhooks and Services
2. Configure an IAM role in AWS account that allows Cloudwatch Logging and S3
list/put/get/delete on the bucket where your content is going
  * The function assumes the bucket name is named the exact same as the repo
name
3. Build a Lambda function that receives events from the SNS Topic.
  * Deploy the built zip from [hugo-lambda-function](https://github.com/jolexa/hugo-lambda-function)
4. Done. Enjoy adding a serverless build system to the pipeline for your
static site.

#### Cost
I mentioned that this is free. It is technically true. My implementation takes
about a minute to run in the worst case (syncing to S3 takes the longest), so
it can run about 53,300 times in a month before I will get charged. That seems
like many, many posts more than I will ever do, I'll optimistically say that
this will get ran 1-4 times per month.

Leave a comment if something should be explained better or use GitHub issues,
otherwise enjoy.
