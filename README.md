# Napp Drawer Module [![gitTio](http://gitt.io/badge.svg)](http://gitt.io/component/com.tiwit)

###Wit.ai

Wit.ai provides a really nice voice api, see: https://wit.ai

Sign up and grab an api key

###This module

Provides Android support, i found issues with their iOS SDK unfortunately

###Methods/Functions

initialize, returns a boolean, a false indicates something has fallen over, i am catching java.lang.Throwable just in case something bad happens

```
require("com.tiwit").initialize("accessToken");
```

startListening, returns a boolean, a false indicates something has fallen over, i am catching java.lang.Throwable just in case something bad happens

```
require("com.tiwit").startListening();
```

stopListening, returns a boolean, a false indicates something has fallen over, i am catching java.lang.Throwable just in case something bad happens

```
require("com.tiwit").stopListening();
```

###Events

witActivityDetectorStarted -- indicates Wit is starting to try and detect voice<br/>
witSuccess -- indicates Wit API has responded, event object will contain message it has interpreted it as<br/>
witFailedToRespondCorrectly -- indicates Wit API has failed to respond, event object will contain message with error message in it<br/>
witDidStartListening -- indicates Wit started listening<br/>

e.g.<br/>

```

var initialized = require("com.tiwit").initialize("accessToken");

if (initialized){

	require("com.tiwit").addEventListener("witSuccess", function(e){
			alert("Wit understood what you said to be: " + e.message);
	});

	require("com.tiwit").addEventListener("witFailedToRespondCorrectly", function(e){
			alert("Wit is not available right now, please try again");
	});

	require("com.tiwit").startListening();

} else {

	console.log("Failed to initialize check adb logs")

}
```

### Get it

Download the latest distribution ZIP-file and consult the [Titanium Documentation](http://docs.appcelerator.com/titanium/latest/#!/guide/Using_a_Module) on how install it

Or simply use the [gitTio CLI](http://gitt.io/cli) [![gitTio](http://gitt.io/badge.svg)](http://gitt.io/component/com.tiwit)

`$ gittio install com.tiwit`

###UI

You'll need to add your own voice button and loading indicator while it processes your voice, it detects when you start and stop talking

## Author

**Louis Quaintance**  
email: louisandkatherine10@gmail.com
