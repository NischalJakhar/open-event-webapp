# Open Event Web App
![Open Event webapp](https://storage.googleapis.com/eventyay.com/assets/branding/webapp_branding.png)

[![Build Status](https://travis-ci.org/fossasia/open-event-webapp.svg?branch=development)](https://travis-ci.org/fossasia/open-event-webapp?branch=development)
[![Heroku](https://heroku-badge.herokuapp.com/?app=opev-webgen-dev)](http://opev-webgen-dev.herokuapp.com)
[![Dependencies](https://david-dm.org/fossasia/open-event-webapp.svg)](https://david-dm.org/fossasia/open-event-webapp)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/c5b7e2ca3e4640c9b38e2f3274072583)](https://www.codacy.com/app/dev_19/open-event-webapp?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=fossasia/open-event-webapp&amp;utm_campaign=Badge_Grade)
[![Code Climate](https://codeclimate.com/github/fossasia/open-event-webapp/badges/gpa.svg?branch=development)](https://codeclimate.com/github/fossasia/open-event-webapp)
[![codecov](https://codecov.io/gh/fossasia/open-event-webapp/branch/development/graph/badge.svg)](https://codecov.io/gh/fossasia/open-event-webapp)
[![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/fossasia/open-event-webapp?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

The **Open Event Web App** project has **TWO** components :
- **An event website generator**
- **The actual generated website output.**

The web generator application can generate event websites by getting data from event `JSON` files and binary media files, that are stored in a compressed zip file. You can also access the application through a `REST API`. Websites that are generated by the "**web app generator**" can be uploaded to any web location, *e.g. on Github pages or any server (e.g. via ftp)*.


## Communication

Please **join our mailing list** to discuss questions regarding the project :

> *https://groups.google.com/forum/#!forum/open-event*

Our chat channel is on **gitter** here:

> *https://gitter.im/fossasia/open-event-webapp*

## 1. Event Website Output

The component that is generated from the web app is the event website. Several sample event sites using the [sample from the open-event repo](https://github.com/fossasia/open-event/tree/master/sample) were generated, showcased on the main index page and added to this repo as a Github Pages site. You can have a look at showcase page on http://fossasia.github.io/open-event-webapp/ We also have a custom domain at http://sched.eventyay.com to which the former link is redirected.

## 2. Web App Generator

### Components and Technology

#### Technologies used

**The webapp generator uses the following technologies :-**

 **1. HTML/CSS/Javascript based frontend**

 **2. [SASS](http://sass-lang.com/)** - *SASS to write optimized CSS.*

 **3. [Node.js](http://nodejs.org)** - *Javascript for the generator backend*

 **4. [Express.js](http://expressjs.com)** - *Server framework*

 **5. [Handelbars](http://handlebarsjs.com)** - *Template for rendering*

 **6. [Socket.io](http://socket.io)** - *For handling multi-user client, with progress of upload/generation*

 **7. [WebdriverJs](https://www.npmjs.com/package/selenium-webdriver)** - *Official Javascript Implementation of Selenium for testing generated event websites*

#### Components of the Generator

**1. Webform**

 > **The source of the webform can be found [here](/src/www).**

**It consists of :-**

 - **[index.html](/src/www/index.html)** - *The webform page*
 - **[form.js](/src/www/js/form.js)** - *The script that uploads the zips, and starts the generator process*

**2. Generator**

The generator runs on a ExpressJS server, using this main [app script](/src/app.js).

**3. Scripts**

 - **[generator.js](/src/backend/generator.js)** - *Does the main generation tasks, and controls other scripts*
 - **[fold_v1.js](/src/backend/fold.js)** - *Groups data of sessions, speakers, tracks etc from JSONs of v1*
 - **[fold_v2.js](/src/backend/fold.js)** - *Groups data of sessions, speakers, tracks etc from JSONs of v2*
 - **[dist.js](/src/backend/dist.js)** - *Creates folders, cleans folders, unzips/zips packages*
 - **[ftpdeploy.js](/src/backend/ftpdeploy.js)** - *Deploys finished website to organiser's server (optional)*
 - **[mailer.js](/src/backend/mailer.js)** - *Sends mail to organiser notifying of successful creation*
 - **[buildlogger.js](/src/backend/buildlogger.js)** - *Displays build logs while generating webapp*
 - **[deploy.js](/src/backend/deploy.js)** - *Automatically deploys generated event sites to user's github account*
 - **[gulpfile.js](/src/backend/gulpfile.js)** - *Creates minified js and css for generated webapp*

**4. Templates**

The HTML pages of the generated website are created using Handelbars templates.

**You can find all the templates [here](/src/backend/templates) -**

  - **footer.hbs** : Common template for footer on all pages
  - **navbar.hbs** : Common template for navbar on all pages
  - **event.hbs** : index.html - Home page
  - **rooms.hbs** : rooms.html - Venues page
  - **schedule.hbs** : tracks.html - Tracks page
  - **speakers.hbs** : speakers.html - Speakers page
  - **session.hbs** : session_id.html - Individual Session page having a particular id
  - **CoC.hbs** : CoC.html - Code of Conduct for an event

**5. Selenium**

  > Contains scripts related to testing different pages of the generated website.

 - **[basePage.js](/src/selenium/basePage.js)** - *Contains methods common to all the pages of the event site*
 - **[eventPage.js](/src/selenium/eventPage.js)** - *Contains methods for testing of the index page of the event*
 - **[trackPage.js](/src/selenium/trackPage.js)** - *Contains methods for testing of the tracks page of the event*
 - **[generatorPage.js](/src/selenium/trackPage.js)** - *Contains methods for testing of the generator form*
 - **[roomPage.js](/src/selenium/trackPage.js)** - *Contains methods for testing of the rooms page of the event*
 - **[schedulePage.js](/src/selenium/trackPage.js)** - *Contains methods for testing of the schedule page of the event*
 - **[sessionPage.js](/src/selenium/trackPage.js)** - *Contains methods for testing of the session pages of the event*
 - **[speakerPage.js](/src/selenium/trackPage.js)** - *Contains methods for testing of the speakers page of the event*

## Other Related Repositories

### Open Event Format Definition

> The **Open Event Project** enables the exchange of data between all components as well as with other services through a standardized Format. The Open Event repository provides a sample implementation of the format. It includes `JSON` files for all relevant event information and binary data for images and audio files.

#### Repository: https://github.com/fossasia/open-event

#### Chat Channel: https://gitter.im/fossasia/open-event

### Open Event Server

> The **Open Event Server** enables organizers to manage events from concerts to conferences and meetups. It offers features for events with several tracks and venues. Event managers can create invitation forms for speakers and build schedules in a Drag & Drop interface. The event information is stored in a database, which can be a `sqlite-db` file or saved in `json` itself. The system provides API endpoints to fetch the data, and to modify and update it. Organizers can import and export event data in a standard compressed file format that includes the event data in `JSON` and binary media files like images and audio.

#### Repository: https://github.com/fossasia/open-event-server

#### Chat Channel: https://gitter.im/fossasia/open-event-server

### Open Event Android App

> The **Open Event Android Project** consists of two components. The **App Generator** is hosted web application, that is hosted on a server and generates an event Android app from a zip with `JSON` and binary files ([examples here](http://github.com/fossasia/open-event)) or through an API. The second component we are developing in the project is generic **Android app** - the output of the app generator. The mobile app can be installed on any Android device for browsing information about the event. Updates can be made automatically through API endpoint connections from an online source *(e.g. server)*, which needs to defined in the provided event zip with the `JSON` files. The Android app has a standard configuration file, that sets the details of the app *(e.g. color scheme, logo of event, link to `JSON` app data).*

#### Repository: https://github.com/fossasia/open-event-android

#### Chat Channel: https://gitter.im/fossasia/open-event-android

**6. Overview Site**

 Contains thumbnail images of sample events and main index.html file required for the [showcase site](http://sched.eventyay.com)

### Web App Generator Test Installation

* You can try out the web generator at https://opev-webgen.herokuapp.com

* The `development-version` is available here: https://opev-webgen-dev.herokuapp.com

* You can use one of the event sample zip files here: https://github.com/fossasia/open-event/tree/master/sample

### Installation/Deployment of the Web App Generator

#### How do I install Web App Generator on a Server

**Please check out [the documentation here](/docs/INSTALLATION.md).**

#### How do I install Web App Generator on my local machine

**Please check out [the documentation here](/docs/INSTALLATION_LOCAL.md).**

#### How do I install Web App Generator on Google Cloud

**To install the system on Google Cloud please refer to the [Google Cloud installation readme](/docs/INSTALLATION_GOOGLE.md).**

#### How do I install Web App Generator on AWS

**To install the system on AWS please refer to the [AWS installation readme](/docs/INSTALLATION_AWS.md).**

#### How do I install Web App Generator on Digital Ocean

**To install the system on Digital Ocean please refer to the [Digital Ocean installation readme](/docs/INSTALLATION_DIGITALOCEAN.md).**

#### How do I deploy Web App Generator with Heroku

**Please read how to deploy to [Heroku here](/docs/INSTALLATION_HEROKU.md)
Or use the 1-click deployment button
[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/fossasia/open-event-webapp/tree/development)**


## Accessing the Generator Web Form

 - Once deployed, you'll find the generator running on http://localhost:5000, it should look like this

![Generator Screencast](docs/screenshots/project.gif)

 - Add your **email id**, select **theme**, select **API version**, select **session style** (single page for each session or expandable sessions), select **data source**

 - Then upload the zip file that contains all JSON files for *speakers*, *sessions*, *sponsors*, *event*, *tracks* and *locations* (These you should get from the server or through the API after you have created your event there).

 - Now, when you click on **GENERATE APP and DOWNLOAD** button, you'll get to download a zip of the event website. You can also deploy the web site to your Github Pages by clicking on **DEPLOY** button.


## Accessing the Generator via REST API

### Endpoints
```
POST /generate
```

**Parameters `(x-www-form-urlencoded)` or `json`**

| Parameter  | Description | Purpose |
|---         |---          |---      |
|name|(required) Name of the webapp   | Unique name of the webapp|
|email|(required) Your email id | We will send a email to this when your webapp is ready|
|datasource | (required) Either `jsonupload` or `eventapi` | |
|apiendpoint| (if datasource = eventapi) API endpoint url | |

**API specifications**

[Postman documenter](https://documenter.getpostman.com/view/1436680/generator/RW89LVYc)

## Configurations

All configurations are saved in the [config.js](/config.json) file.

NOTE: In this document all `config.<obj>` variables refer to the data in the *config.json* file.

### Server Configs

#### PORT
| Variable | Description |
| ----     | ----        |
`process.env.PORT` |(Can be described in shell env, or in Heroku type platforms)
`config.PORT` |(Falls back to config file if above not found)

#### Mailer
We use **Sendgrid** to send mails, and you need a `Sendgrid API` to make it work. Additionally, you can also use `SMTP` to send mails if you don't have `Sendgrid Key`.

| Variable | Description |
| ----     | ----        |
`process.env.SENDGRID_API_KEY` | (Tries to get from shell env first)
`config.SENDGRID_API_KEY` | (Falls back to config file)
`process.env.SMTP_USERNAME` | (Tries to get from shell env first)
`config.SMTP_USERNAME` | (Falls back to config file)
`process.env.SMTP_PASSWORD` | (Tries to get from shell env first)
`config.SMTP_PASSWORD` | (Falls back to config file)

### Upload

- We use **AWS S3 services** for storing the zip file of the generated event. These zip files are automatically deleted after 3 days from the store.

- Each uploaded file has a unique download link. `node-uuid` module is used for generating the cryptic download link of the file.

| Variable | Description |
| ----     | ----        |
`process.env.AWS_BUCKET` | (Tries to get from shell env first)
`config.AWS_BUCKET` | (Falls back to config file)
`process.env.AWS_ACCESS_KEY_ID` | (Tries to get from shell env first)
`config.AWS_ACCESS_KEY_ID` | (Falls back to config file)
`process.env.AWS_SECRET_ACCESS_KEY` | (Tries to get from shell env first)
`config.AWS_SECRET_ACCESS_KEY` | (Falls back to config file)

### Github Deploy

The web-app is able to automatically deploy the generated event sites to Github Pages of a User. We use `passport` library for authentication of the user. For uploading and committing the event files, we use `github` library which provides a wrapper for the **Github API** in `node`.

| Variable | Description |
| ----     | ----        |
`process.env.GITHUB_CLIENT_ID` | (Tries to get from shell env first)
`config.GITHUB_CLIENT_ID` | (Falls back to config file)
`process.env.GITHUB_CLIENT_SECRET` | (Tries to get from shell env first)
`config.GITHUB_CLIENT_SECRET` | (Falls back to config file)
`process.env.CALLBACK_URL` | (Tries to get from shell env first)
`config.CALLBACK_URL` | (Falls back to config file)


#### Images

**We need to process all the speaker images and there are certain configs used -**

| Variable | Description |
| ----     | ----        |
`config.speaker_images.MAX_WIDTH` |(Max needed height of speaker image)
`config.speaker_images.MAX_HEIGHT` |(Max needed width of speaker image)
`config.speaker_images.TRACK_HEIGHT_REM` |(Speaker image height, in CSS rem units, for tracks page)
`config.speaker_images.TRACK_WIDTH_REM` |(Speaker image width, in CSS rem units, for tracks page)

#### Audio

**Some sessions can have a recorded audio attached to them. The parameters for that are -**

| Variable | Description |
| ----     | ----        |
`config.audio_files.MAX_SIZE_MB` | Max size of the audio (limited by Github file size)


## Contributions, Bug Reports, Feature Requests

> This is an Open Source project and we would be happy to see contributors who report bugs and file feature requests submitting pull requests as well.

**Please report issues [here](https://github.com/fossasia/open-event-webapp/issues)**


## Issue and Branch Policy

> Before making a pull request, please file an issue. So, other developers have the chance to give feedback or discuss details. Match every pull request with an issue please and add the issue number in description e.g. like "**Fixes #123**".

**We have the following branches :-**
 * **development**
	 All development goes on in this branch. If you're making a contribution,
	 you are supposed to make a pull request to _development_.
	 PRs to master must pass a build check and a unit-test (_test/serverTest.js_) check on Travis
 * **master**
   This contains shipped code. After significant features/bugfixes are accumulated on development, we make a version update, and make a release.

## Contributions Best Practices

  **Commits**
 * Write clear, meaningful git commit messages (Do read http://chris.beams.io/posts/git-commit/)
 * Make sure your PR's description contains GitHub's special keyword references that automatically close the related issue when the PR is merged. (More info at https://github.com/blog/1506-closing-issues-via-pull-requests )
 * When you make minor changes to a PR (like for example fixing a failing Travis build or some small style corrections or minor changes requested by reviewers) make sure you squash your commits afterward. (Learn how to squash at https://davidwalsh.name/squash-commits-git )
 * When you're submitting a PR for a UI-related issue, it would be great if you add a screenshot of your change or a link to a deployment where it can be tested out along with your PR.

 **Feature Requests and Bug Reports**
 * When you file a feature request or when you are submitting a bug report to the [Issue tracker](https://github.com/fossasia/open-event-webapp/issues), make sure you add steps to reproduce it.

 **Join the development**
 * Before you join development, please set up the project on your local machine, run it and go through the application completely. Press any button that you can see and see where it leads. Explore. (Don't worry, Nothing will happen to the app due to the exploring: wink: The only thing that will happen is, you'll be more familiar with what, is where and might even get some cool ideas on how to improve various aspects of the app.)
 * If you would like to work on an issue, drop in a comment on the issue.

 Do read the [Open Source Developer Guide and Best Practices at FOSSASIA](https://blog.fossasia.org/open-source-developer-guide-and-best-practices-at-fossasia).


## Testing locally

If you want to run tests locally, first install the following:

    npm install --no-save mocha chromedriver

You can then run the full test suite with:

    npm test

or you can run one individual test script like this:

    npx mocha -b test/generatorAndSchedule.js


## LICENSE

OpenEvent Webapp - A webapp and it's generator, written under the FOSSASIA Open Event project. The Open Event project aims to make server and client software required for hosting events/conferences easy to build and configure. Copyright (C) 2016, FOSSASIA. This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version. This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details. You should have received a copy of the GNU General Public License along with this program.  If not, see <http://www.gnu.org/licenses/>.

## Maintainers

**The Project is maintained by :-**

- **Arnav Gupta ([@championswimmer](https://github.com/championswimmer))**
- **Aayush Arora ([@aayusharora](https://github.com/aayusharora))**
- **Mario Behling ([@mariobehling](http://github.com/mariobehling))**
- **Justin Lee ([@juslee](http://github.com/juslee))**
