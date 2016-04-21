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
}
```

###UI

You'll need to add your own voice button and loading indicator while it processes your voice, it detects when you start and stop talking
