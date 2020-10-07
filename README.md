# firebase-login
Login using Gmail and password
// 1 . Create a Firebase developer account at https://firebase.google.com/ and click on 'GO TO CONSOLE'
// 2 . Click on 'Add project'.
// 3 . Select the 'Android' platform SDK.
// 4 . Open Android project.
//     Open the Gradle tab from a right side panel.
//     Double click on 'signingReport'.
//.    Sha-1 key is optional.
build.gradle(Project)

dependencies {  

    classpath 'com.android.tools.build:gradle:3.0.1'  

    classpath 'com.google.gms:google-services:4.0.1'  

  

    // NOTE: Do not place your application dependencies here; they belong  

    // in the individual module build.gradle files  

}  

build.gradle (Module)

dependencies {  
    implementation fileTree(dir: 'libs', include: ['*.jar'])  
    implementation 'com.android.support:appcompat-v7:27.1.1'  
    implementation 'com.android.support.constraint:constraint-layout:1.1.3'  
    testImplementation 'junit:junit:4.12'  
    androidTestImplementation 'com.android.support.test:runner:1.0.2'  
    androidTestImplementation 'com.android.support.test.espresso:espresso-core:3.0.2'  
    implementation 'com.google.firebase:firebase-auth:16.0.3'  
    implementation 'com.google.firebase:firebase-core:16.0.3'  
    implementation 'com.google.android.gms:play-services-auth:16.0.0'  
    implementation 'com.github.bumptech.glide:glide:3.7.0'  
}  
apply plugin: 'com.google.gms.google-services'  


android mainfest.xml

     <uses-permission android:name="android.permission.INTERNET" />  
     
// on main activity.java

mAuth.createUserWithEmailAndPassword(email, password)

        .addOnCompleteListener(this, new OnCompleteListener<AuthResult>() {

            @Override

            public void onComplete(@NonNull Task<AuthResult> task) {

                if (task.isSuccessful()) {

                    // Sign in success, update UI with the signed-in user's information

                    Log.d(TAG, "createUserWithEmail:success");

                    FirebaseUser user = mAuth.getCurrentUser();

                    updateUI(user);

                } else {

                    // If sign in fails, display a message to the user.

                    Log.w(TAG, "createUserWithEmail:failure", task.getException());

                    Toast.makeText(EmailPasswordActivity.this, "Authentication failed.",

                            Toast.LENGTH_SHORT).show();

                    updateUI(null);

                }

                // ...

            }

        });
