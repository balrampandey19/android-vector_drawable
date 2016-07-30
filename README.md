#Android Vector Drawable Support 23.2.0

####Support Vector Drawables and Animated Vector Drawables


Vector drawables allow you to replace multiple png assets with a single vector graphic, defined in XML. While previously limited to Lollipop and higher devices, both VectorDrawable and AnimatedVectorDrawable are now available through two new Support Libraries support-vector-drawable and animated-vector-drawable, respectively.

Android Studio 1.4 introduced limited support for vector drawables by generating pngs at build time. To disable this functionality (and gain the true advantage and space savings of this Support Library), you need to add vectorDrawables.useSupportLibrary = true to your build.gradle file:

```
 // Gradle Plugin 2.0+  
 android {  
   defaultConfig {  
     vectorDrawables.useSupportLibrary = true  
    }  
 } 
 ```
 
  You’ll note this new attribute only exists in the version 2.0 of the Gradle Plugin. If you are using Gradle 1.5 you’ll instead use

 ```
Gradle Plugin 1.5  
 android {  
   defaultConfig {  
     generatedDensities = []  
  }  

  // This is handled for you by the 2.0+ Gradle Plugin  
  aaptOptions {  
    additionalParameters "--no-version-vectors"  
  }  
  
 }  
 ```
 
 You’ll be able to use VectorDrawableCompat back to API 7 and AnimatedVectorDrawableCompat on all API 11 and higher devices. Due to how drawables are loaded by Android, not every place that accepts a drawable id (such as in an XML file) will support loading vector drawables. Thankfully, AppCompat has added a number of features to make it easy to use your new vector drawables.

Firstly, when using AppCompat with ImageView (or subclasses such as ImageButton and FloatingActionButton), you’ll be able to use the new app:srcCompat attribute to reference vector drawables (as well as any other drawable available to android:src):

 ```
<ImageView  
  android:layout_width="wrap_content"  
  android:layout_height="wrap_content"  
  app:srcCompat="@drawable/ic_add" />  
  
   ```
   
   And if you’re changing drawables at runtime, you’ll be able to use the same setImageResource() method as before - no changes there. Using AppCompat and app:srcCompat is the most foolproof method of integrating vector drawables into your app.
   
   
   
 ```
   Copyright 2016 Balram Pandey

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.'

 ```
 
[www.balrampandey.com](wwww.balrampandey.com)
