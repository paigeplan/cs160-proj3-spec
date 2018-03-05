Tip: Try to get your firebase console set up early. 


Before you start:
- To set up a Firebase console, you’ll need a Google account. You can use any google account for this.



### Getting started 
If you haven’t already, create a new Android Studio project as you would normally. 

## Setting up the Realtime Database
### Part 1: Connect your app to Firebase

1. Open the Firebase Console from the Tools menu: **Tools > Firebase**
2. You should see a list of Firebase features. For this assignment, we’ll just be using the Realtime Database to store data shared among users. (extra credit for authentication?). Select **Realtime Database** from the list, and then click **Save and Retrieve Data**
3. Select **Connect Your App to Firebase**
4. If prompted, sign in to the account you want to use with Firebase, select **Create a new Firebase Project** and then **Connect to Firebase**.

After this step, you should see a project with the name your provided here:  https://console.firebase.google.com/. 

### Part 2: Add the Realtime Database to your App
5. Back in Android Studio, select **Add the Realtime Database to your app**. 

> You may get a warning about your google-services plugin version here. If so, open your app/build.gradle file. Make sure all the plugins listed under "dependencies" have the same version (most likely, you'll want to update your firebase database library to the most recent version 11.8.0. by editing the "com.google.firebase:firebase-database:X.X.X" string).  

If you have no errors after building your app, move on to step 3 in your Firebase Console.


### Part 3: Configure Firebase Database Rules
TODO

### Part 4: Write to your Database
Use the example code provided to test that writing to your database will work. To test that your database works, but the code snippet provided in this section in your `onCreate` method.





You can follow the instructions in Android Studio or online here: https://firebase.google.com/docs/database/android/start/
