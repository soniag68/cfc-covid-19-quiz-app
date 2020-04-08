### Call for Code 2020 - Quiz App Starter Kit

This is a very simple example quiz application that uses a Loopback generated express app with a react frontend.

As learning and collaboration moves online in response to the coronavirus and COVID-19 pandemic, developers need to build microservices to enable distance learning. As part of that learning, instructors need to be able to assess their students' understanding of course material.

This tutorial shows you how to build a simple quiz app to assess learner understanding. A major benefit of the app is its flexibility: this starter kit can easily be adapted into a short essay app, a grading app, or other educational tool.

Loopback is an open source tool for quickly building a data api for your applications. Whatever your specific application's purpose, Loopback gets you quickly writing application logic instead of data-handling code.

![Quiz app interface](images/quiz-app.png)

You can find code and related files for this tutorial in the accompanying <a href="https://github.com/Call-for-Code/cfc-covid-19-quiz-app" target="\_blank">GitHub repo</a>.

You can also [try a quiz](http://nibz-falco-test-2-5290c8c8e5797924dc1ad5d1b85b37c0-0000.us-east.containers.appdomain.cloud/index.html) and [explore the api](http://nibz-falco-test-2-5290c8c8e5797924dc1ad5d1b85b37c0-0000.us-east.containers.appdomain.cloud/explorer/) before you get started on your own app.


## Learning objectives

By completing this tutorial, you will learn how to create a simple example quiz application that uses a Loopback-generated Express app with a React front end.

## Prerequisites

The core of this example is *generated code* from the Loopback utility. For clarity, we're using the now-deprecated version 3.0 of the Loopback library. This makes the app easier to start, but you should consider upgrading to Loopback v4 to get the latest features and security updates.

## Estimated time

Completing this tutorial should take about 30 minutes

## Architecture diagram

![Quiz app architecture diagram](images/cfc-covid19-remote-education-diagram-1.png)

1. The user navigates to the site.
2. The user is presented with a website, a React front end.
3. (a) The user performs an action within the Express app. (b) The LoopBack-generated code performs the necessary task within the Express app.
4. Changes are saved in a PluggableDB.


## 1. Set up your environment

To get the most out of this starter kit, you should consider creating your own Loopback app. [It's super fast!](https://www.youtube.com/watch?v=iOMD27DjuO4). 

However, to start this app, use the following steps. (**Note**: To use pre-created data and React builds, see [Quickstart instructions](#quickstart-instructions), below.)

1. Run the following commands.

   ```bash
   npm install
   npm start
   ```
   
2. When the API is up, navigate to the Swagger API explorer at <https://localhost:3030/explorer>. From there, you can start to add data into your API right away. 

    ![Swagger API explorer - adding data](images/quiz-app-2.png)

3. Create a quiz using this JSON blob:

  ```json
  {
    "author": "Scientist's Limited",
    "title": "Eight Science Questions You Don't Know the Answer to",
    "pass_pct": 0.8
  }
  ```

   ![Swagger API explorer - creating a quiz](images/quiz-app-4.png)

4. Create a question using this JSON blob:

   ```json
   {
     "question_text": "Which immobile ground unit has the longest range?",
     "answers": [
       "Siege Tank",
       "Spore Colony",
       "Photon Cannon",
       "Bunker (Marines"
     ],
     "correct_answer_index": 0,
     "quizId": 1
   }
   ```
   
    ![Swagger API explorer - creating a question](images/quiz-app-3.png)

## 2. Create the app front end

The app front end is coded in [React](https://reactjs.org/), a library for user interfaces. If you don't have experience with React, or if you want to use something simpler, you can achieve similar results using tools such as [Bootstrap](https://getbootstrap.com/) and [jQuery](https://jquery.com/). The front-end code is compiled once and then served by the Express app generated by Loopback.

To build and install the front-end code, run the following commands:

```bash
cd frontend
npm install
SKIP_PREFLIGHT_CHECK=true npm run build
# this creates a build in build/
rm -fr ../public/*
cp -r build/* ../public/
# restart the app
```

To connect to the frontend access <http://localhost:3030/index.html>


### 3. Deploy on IBM Cloud

Because this is a standard Express application, you can use either Cloud Foundry or Kubernetes to host it.  A Dockerfile is included.

* To deploy using cloud foundry, follow [these steps](https://github.com/IBM/nodejs-express-app#ibm-cloud-developer-tools).

* To deploy using Kubernetes, use the included manifest in `deployment/deploy.yaml`. **Note**: If you are using Ingress, you must populate the Ingress hostname with the Ingress subdomain of your cluster. For example:


    ```
    $ ibmcloud ks cluster get --cluster nibz-falco-test-2 | grep Ingress
    Ingress Subdomain:              nibz-falco-test-2-5290c8c8e5797924dc1ad5d1b85b37c0-0000.us-east.containers.appdomain.cloud
    ```


## Quickstart instructions

To by-pass all the previous steps and start *extremely* quickly (although we'd rather you learn the previous steps first!), you can use pre-loaded data and a pre-built build of the front-end code:

    ```
    npm install
    cp examples/data.db data.db
    cp -r examples/public/* public/
    npm start
    ```

## Summary

In this tutorial, you've learned how quickly you can create and configure an app to assess how well students have absorbed instructional material. You've also seen how simple it is to adapt the quiz app to other educational requirements. You have have everything you need to create a simple, flexible tool to assist teachers and students who are making an unprecedented shift to online learning.


