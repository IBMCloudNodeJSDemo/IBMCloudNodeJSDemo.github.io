---
layout: lab
title: Consuming Cloud Services
---

## Introduction

The IBM Cloud platform (like other cloud platforms) provides a huge set of services
that can be used as ready to use building blocks to enhance your application.

These services typically only have to be instantiated and configured to be used.

Such a service might be a database engines like Cloudant, and IOT platform,
a mobile services that send push notification or might provide to artificial intelligence capabilities like the Watson Tone Anaylzer used in this exercise.

The Watson Tone Anaylzer service is able to detect moods and tones in a text submitted to it.

In this exercise you will instantiate an instance of the Watson Tone Analyzer Service and connect it to a simple app that is provided to you in a Github Repository.

The purpose of this exercise is to enable you to configure and use existing cloud services to add value to your application without much work.

## Subscribe to the IBM Tone Analyzer Service

- Go to the _IBM Cloud_ main menu and click on **Catalog**,

  ![catalog](lab4_catalog.png?raw=true)

- Select **Watson** in the menu on the left side

  ![watson](lab4_watson.png?raw=true)

- Click on **Tone Analyzer**

  ![tone](lab4_tone_tile.png?raw=true)

- On the next page leave all default values as they are and click **Create**

  Wou will get redirected to another page. At this point of time the service is ready to use

- Retrieve the credentials for your service instance

    1. Click Service credentials.
    1. Click View credentials under Actions.
    1. Copy the username, password and values.

- Note the values to be used in the next section

## Get the code of the sample app

The sample app uses the Watson Tone Analyzer service to score lines of text as happy or unhappy.
The app provides a basic user interface and an API that you will use in an later excercise.

- Fork the git repository [linked here](https://github.com/IBMCloudNodeJSDemo/NodeJSDemo) into your own Github account by pressing the **Fork** button in that Github Repository

  ![fork](lab4_fork.png?raw=true)

- Copy the URL of your repository from the Github UI

  ![clone](lab4_clone.png?raw=true)

- Clone your fork of the repository to your local disk

  ```bash
  git clone <url from the last step> and change into the created folder
  ```

- Copy the file `.env.sample` and save it under the new name `.env`

- Edit the new file `.env` and fill in username, password and url of your instance of the Tone Analyzer service

# Test the app locally

- Install dependent packages via: `npm i`
- Start the app via: `node app.js`
- You can open the app by visiting [http://localhost:3000](http://localhost:3000) in your browser
- Press the submit button on the loaded page. Enter the word "happy" in the mood field
- You can play around by changing the content of the input fields

Disclaimer: The scoring algorithm that condenses of the complex response of the Tone Analyzer service to one single word is quite simple and might return surprising results. Feel free to improve.

![toneapp](lab4_toneapp.png?raw=true)

# Push the working app to IBM Cloud

In the root directory of the app create a file named `manifest.yml` with the following content:

  <pre>
      ---
      applications:
      - name: <span class="app_name"><span class="app_name">random-app-name</span></span>
        memory: 128M
        host: <span class="app_name"><span class="app_name">random-app-name</span></span>
  </pre>

- Set the API endpoint to your region

  ```bash
  cf api api.eu-de.bluemix.net
  ```

- login into the IBM Cloud using your credentials

  ```bash
  cf login
  ```

- target your organisation and space

  ```bash
  cf target -o <YOUR ORG> -s <YOUR SPACE>
  ```

- Deploy your app to the cloud

  <code>
  cf push
  </code>

- Access the app in your browser as https://<span class="app_name">random-app-name</span>.eu-de.bluemix.net

- Submitting with all defaults should again return "happy" in the mood field

## References

* [Source code of the demo application](https://github.com/HRTCloudDemo/HRTToneDemo)
* [Watson Tone Analyzer](https://www.ibm.com/watson/services/tone-analyzer/)
* [Watson Tone Analyzer Documentation](https://console.bluemix.net/docs/services/tone-analyzer/index.html#about)
* [More complete sample app on Github](https://github.com/watson-developer-cloud/tone-analyzer-nodejs)

{% include random_app_name.html %}
