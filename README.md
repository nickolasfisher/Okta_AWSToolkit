## Purpose

This application is written to demostrate wrintg a .Net 5 application with ASP.Net Core 5.  The application is secured with Okta.  The tutorial that follows is for publishing the application to Elastic Beanstalk using the AWS Toolkit for Visual Studio 2019.

## Requirements

> Visual Studio 2019

> .NET 5

> [An Okta Developer Account](https://developer.okta.com/signup/)

> [The Okta CLI tool](https://developer.okta.com/blog/2020/12/10/introducing-okta-cli)

> An AWS Account

## Instructions

Download the code

Download the AWS Toolkit for Visual Studio 2019

Go through the *Getting Started with the AWS Toolkit for Visual Studio* screen in the AWS Toolkit

Right click on your project and select **Publish to AWS Elastic Beanstalk**

Under the Application tab, select *Create a new application environment*

Under the Application Envinronment tab, select the production version of your application.  Note that you will need to change the url that is populated by default since it using the project name.  Pick a URL that is specific to you.  Make note of this URL as well as you will need it when setting up your Okta application.  

Under the AWS Options tab, set your instace type to t2.micro to stay on the free tier in AWS. 

Under the options tab, use the release configuration.  

Press **Finish**  and wait for the application to deploy.

## With the Okta CLI

Run the command okta apps create

 > Select Web as the application Type
 
 > Select Other as Type of application
 
 > For Redrecition URI, use the domain you created when publishing to Elastic Beanstalk appended with `/okta/callback`
 
 > For Post Logout Redirect URI use the same domain but appended with `/signout/callback`
 
 > For Authorization Servers (if multiple) use default

Open the file `.okta.env` which should have your *ClientId*, *Client Secret*, and *Issuer*

## In Visual Studio

Create appsettings.Production.json

Copy the JSON from appsettings.json

Replace ClientId value with the *ClientId* from `.okta.env`

Replace Client Secret value with the *Client Secret* from `.okta.env`

Replace Domain value with the domain part of your Issuer, not the full Issuer

## Publish to AWS

Go through the publish to Elastic Beanstalk workflow again, this time selecting *Redeploy to an existing environment*

