#Base App - Android
#####Copyright (C) 2017 Attinad Software Pvt Lmt.

Base App is an custom template for Android projects, Which is created by following common packaging structure used for Android apps so that projects build on this can also follow the same. The application architecture is up to the developer (Strongly recommend [MVP](http://konmik.com/post/introduction_to_model_view_presenter_on_android/) instead of MVC ). In addition the **Base App** also contains basic features of an Android app. 

###Package Structure

The **Base App** uses following packaging structure.

```
com.attinad.baseapp.template
├─ api
	├─ RestClientHolder
	└─ Rest Client interfaces ..
├─ constants
├─ enums
├─ exceptions
├─ interfaces
├─ model
├─ managers
├─ utils
├─ service
	├─ ServiceHolder
	└─ Service interhces and implementations ..
└─ views
   ├─ adapters
   ├─ actionbar
   ├─ widgets
   └─ notifications
```

> **Note:** If you are implementing a new feature its always better to keep feature related classes in same package. See ***cache*** package in **BaseApp**

###Packages

####api
This is where the api clients are defined.  There is a class called `RestClientHolder.class` which have reference to all api clients defined in this package. Please see sample api clients defined in the **Base App**

####service
Service interfaces and their implementations are defined in this package. The service interfaces can be User service, VOD service, Configuration services etc. The service implementation can implement more than this service interfaces. Like if single back-end server handles both the User service and Configuration service then there need to be single service implementation  that implements these two.  Please 

The reference to each service is kept in `ServiceHolder.class`.


> **Note:**

> - Always follow [code to interfaces](http://www.javaworld.com/article/2076468/core-java/smarter-java-development.html) on defining services. 
> - Its better to define services in the basis of purpose. Like ***UserService*** interface should only contains methods related user data, ***ConfigurationService***  interface contains methods related to fetching configuration. This way services are kept as modules and  corresponding implementations are decoupled with other managers using this services.

####manager
This package contains your manager implementations. Its recommended that the business logic should be implemented in the manager class itself instead of the views.

####Model
The model classes are added in this package. Later it will be helpful for [obfuscation](https://developer.android.com/studio/build/shrink-code.html).


####util
Common util classes used through out the applications are placed here.


###External Tools 
Base app is packed with common tools used in android development

####Cache Management
Abstract methods are included for the File cache management and Disk Lru cache management. see package ***cache*** for details

####Image Processing
[Glide](https://github.com/bumptech/glide) by Google Inc. is used for image processing in this application. Other suggestion is [Fresco](https://github.com/facebook/fresco) by Facebook Inc.  which is more memory efficient and supports extensive customization of image loading and display.


####Networking
Android HTTP client library [Retrofit](https://github.com/square/retrofit) by Square Inc. is used for networking.
 

