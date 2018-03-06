Tip: Try to get your firebase console set up early. 


Before you start:
- To set up a Firebase console, you’ll need a Google account. You can use any google account for this.

### Getting started 
If you haven’t already, create a new Android Studio project as you would normally. 

## Setting up the Realtime Database
### Part 1: Connect your app to Firebase

1. Open the Firebase Console from the Tools menu: **Tools > Firebase** You should see a list of Firebase features. For this assignment, we’ll just be using the Realtime Database to store data shared among users. (extra credit for authentication?).
2. Select **Realtime Database** from the list, and then click **Save and Retrieve Data**
![](img/connect.png)
3. Select **Connect Your App to Firebase**
4. If prompted, sign in to the account you want to use with Firebase, select **Create a new Firebase Project** and then **Connect to Firebase**.

After this step, you should see a project with the name your provided here:  https://console.firebase.google.com/

### Part 2: Add the Realtime Database to your App
5. Back in Android Studio, select **Add the Realtime Database to your app**. 

> You may get a warning about your google-services plugin version here if you used a Map template. If so, open your app/build.gradle file. Make sure all the plugins listed under "dependencies" have a the same version. This version should be less than or equal to your device's Google Play Services Version.

You should not see any errors after building your app at this point. 

### Part 3: Configure Firebase Database Rules
Firebase allows you to set permissions for who can read and write to your database. By default, this is set to private (only authenticated users can read and write to the database). Since there is no authentication required in this app so far, you'll need to set read and write to public.
1. Open up your project via the online Firebase Console: https://console.firebase.google.com/
2. Select **Database** > **RealtimeDatabase** 
![](img/database.png)
3. Open the **Rules** tab, and set both read and write permissions to public:
     
       {
          "rules": {
            ".read": true,
            ".write": true
          }
        }

### Part 4: Write to your Database
In the firebase database, data is written to **references** using the `setValue` function. Here's an example of writing data to your database. 

    // entry point to access your Firebase database
    FirebaseDatabase database = FirebaseDatabase.getInstance();

    DatabaseReference dogsRef = database.getReference("Dogs");  // ~/Dogs
    
    // use the `child` method to nest data
    DatabaseReference molly = dogsRef.child("Molly");           // ~/Dogs/Molly/
    molly.child("age").setValue(13);                            // ~/Dogs/Molly/age = 13
    molly.child("toy").setValue("lemon");                       // ~/Dogs/Molly/toy = lemon


1. To test that your database is working, try writing to your database in your `onCreate` method.
2. Run your app, and check that your database contains the data you provided. Below is the output of the code posted above, with one extra dog.

![](img/write_example1.png)

3. You aren't just limited to strings and ints! Check out other writeable types here: https://firebase.google.com/docs/database/admin/save-data. Writing custom Java objects to your database is a great way to cut down on the amount of code you need to write. 

### Part 5: Read from your Database

> See [Listen for value events](https://firebase.google.com/docs/database/android/read-and-write) for an example of a Post listener.

#### Terms
- **ValueEventListener** - To read data from your Firebase Database, you'll want to use *ValueEventListeners*. Like *OnClickListeners*, *ValueEventListeners* continuously "listen" for a certain event. While *OnClickListeners* recieve button click events (with `onClick` as the callback), *ValueEventListeners* receive events whenever the data in your database changes (with `onDataChange()` as the callback).

This is perfect for a message based app - whenever someone posts a message, all users should re-read from the database, so that they are all up to date.


##### Simple Example
For this example, I'll use this Firebase Database. Add a data tree to your database using Android or using the online console.

     {
       "Dogs" : {
         "Molly" : {
           "age" : 13,
           "toy" : "lemon"
         },
         "Puff" : {
           "age" : 8,
           "toy" : "chess set"
         }
       }
     }

     
1. In MainActivity, add the following code:

          ValueEventListener myDataListener = new ValueEventListener() {
              @Override
              public void onDataChange(DataSnapshot dataSnapshot) {
                  // TODO: do something with data
              }

              @Override
              public void onCancelled(DatabaseError databaseError) {
                  //
               };

               mPostReference.addValueEventListener(postListener);


    


You can follow the instructions in Android Studio or online here: https://firebase.google.com/docs/database/android/start/
