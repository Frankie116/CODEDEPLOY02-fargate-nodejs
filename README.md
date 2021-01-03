# ---------------------------------------------------------------------------------------------------
# version  1.0
# Library: https://github.com/Frankie116/my-library.git
# Project: CP07-fargate-nodejs
## Purpose: This project creates a loadbalanced fargate infrastructure using AWS CodePipeline.  The infrastructure is used to host a simple node.js app that is hosted in duplicate containers in redundant availablity zones. The Docker images are built locally and pushed to AWS ECR.  These are then used by AWS ECS to host the apps.
   Author:  Frank Effrim-Botchey
## ----------------------------------------------------------------------------

This project is part of an AWS CodePipeline which monitors changes in this git repo.

The following is performed when changes are detected in the repo.

  [1] CodePipeline connects to this github repo and uses the buildspec.yml & Dockerfile to build a new docker image using CodeBuild.
  
  [2] CodePipeline pushes the new image to AWS ECR Repository.
  
  [3] Codepipeline directs ECS to retrieve the image from ECR and starts to create the aws cloud infrastructure.
  
  [4] ECS then runs the app inside docker containers hosted on load balanced infrastucture publicly accessible in the aws cloud..
