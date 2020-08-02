---
layout: post
title:      "Workout Tracker - Sinatra Portfolio Project"
date:       2020-08-02 00:32:37 +0000
permalink:  workout_tracker_-_sinatra_portfolio_project
---

Bodybuilding has been a passion of mine ever since the first year of college. It allows one to continually push the limits of one's physical strength as well as trains the mind in discipline and fortitude. Bodybuilding is a gradual process, nobody sees results overnight or even for weeks. I've used countless applications to track my body's progression over time, and I thought it was long overdue for me to create a workout tracker to keep track of my lifts for my Sinatra Portfolio Project.


First I sat down to plan out how I wanted to design my workout tracker application. I designed  the Models needed for the project: User and Workout. Next, I took to creating the database schema for both of my models. At first I had trouble figuring out how I wanted to store my exercises within Workouts, but I figured out how to save Arrays into my database from trusty ol' StackOverflow. Mapping out the has_many and belongs_to relationship mappings was easy, as the labs prepared me with a solid foundation of the different relationships. 


After creating the workout_controller and user_controller, I started with the login/signup/logout routes for the user. 
This portfolio project tested my knowledge of user authentication and keeping an active session for the user who was logged in. I set the user's ID into the session whenever a valid user sign-up occurs, and that user would stay in session until the user wishes to logout. Upon logging in, I authenticated the user's stored password with the password passed through the params value, and if successful I would then set the session ID to that specific user ID.

Once this was finished, I started on the RESTful routes for my workout_controller. I had to ensure that users weren't able to view, edit, or delete other workouts created by other users. To do so, I created a check to see if current user matched that of the user who created the workout:

``` if logged_in? && @workout.user == current_user ``` 

Another obstacle in developing this app was figuring out how to prevent empty parameters when a user signs up or when a user creates/edits a workout. I did not want any empty workouts nor empty user accounts. I added a method in User and Workout to determine whether or not there exists an empty parameter. If the check failed, then I would route the user back to their corresponding previous page. 

``` def self.valid?(params)
        return !params[:name].empty? && !params[:email].empty? && !params[:password].empty?
    end```


Over several iterations of testing and tweaking, I had implemented a fully working workout tracker. My workout tracker had the ability to create a workout with a title, date of workout, and a list of exercises, but I wanted to also keep track of the weights lifted for each of these workouts. I refactored my schema to include an array of weights and edited each of my .erb files to reflect the additional parameter. In the future I wish to continue developing this application and make it beautiful with some minimalist CSS, but I have much to learn about CSS and the frontend so it will be a journey.

Github Repo: [`Workout Tracker`](https://github.com/marcusLau/workout_tracker)
