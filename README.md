# Make your first Voice Call with MessageBird
### ⏱ 10 min build time

It's time to make your first voice call using the [MessageBird Voice
API](https://developers.messagebird.com/docs/voice-calling)! Before we
get started, have you set up your Python development environment with the MessageBird Python client? 

- **No** - make sure you [read this MessageBird Developer Guide](https://developers.messagebird.com/guides/setup-local-dev-environment) before getting started. 
- **Yes!** - Great! Now you can make your first API request and make a voice call with MessageBird using Python.

## Getting started

First, let's create a new Python project directory. In this directory, create a `voice_call.py` file and open it in your text editor of choice. Start by importing the MessageBird Python library and creating an instance of the MessageBird client:

````python
import messagebird

#create instance of messagebird.Client using API key
client = messagebird.Client('your-api-key')

````

Note that you can create either a **test** or **live** API key:

- **test** API keys simulate responses from the MessageBird server, allowing you to test your code flow and error handling before sending real messages. (You still must have an internet connection to use MessageBird REST API features.)
- **live** API keys allow you to send actual messages to your recipients. We recommend that you do not publish this key anywhere.

In order to start using the SDK, replace `your-api-key` with your API
key. 

**Pro-tip:** Here, we're hardcoding your API key in your program to keep the guides straightforward. But for production applications, we recommended storing
the key in a configuration file or environment variable instead and passing the variable to your application. You'll see this in
practice later in our MessageBird Developer Guides for common
use cases.

## Making a voice call

Now we can attempt create a voice call with a message as follows:

````python
try:
    msg = client.voice_message_create('+319876543211', 
    	  'Hey you, a little bird told me you wanted a call!',
    	  { 'voice' : 'male' })
    print(msg.__dict__)

````

Here, we're calling `voice_message_create()` with these parameters:

- The first parameter is the recipients phone number, including the country code.
- The second parameter is the message that the recipient will hear on the call.
- The third parameter is a Python dictionary containing optional attributes that you can specify for this phone call. Here, we're setting one of the optional attributes, the gender of the voice in the call, to "male". You can find more information about other optional attributes in the [Voice Calling API Reference](https://developers.messagebird.com/docs/voice-calling#calls).

If the call succeeds, the application will print details about the call to the console.

We've used an example phone number for the recipient's phone number. For your application to work, you should replace this number with a working number.

If the attempt to create a voice call fails, we print the errors to the console with the following clause:

````python
except messagebird.client.ErrorException as e:
    for error in e.errors:
        print(error)
````

## Finishing your program

Once you've done all that, you have a fully functioning Python program that makes a call to your set destination phone number when run.

To test your application, run in the terminal:

````bash
python voice_call.py
````

If everything worked, you should see the API response logged in the terminal, signalling that you've successfully made a call.

If you used a live API key and had verified your number or added credits to your account,
your phone will ring shortly and deliver the message when you pick up the phone. 
Congratulations, you just initiated your first voice call with MessageBird!

If you see an error from the script, try to read and understand the
message and fix the problem.

Next steps
----------

Let's head over to the next **MessageBird Developer Guide** learn how
to [set up and handle incoming voice
calls](https://developers.messagebird.com/guides/handle-incoming-calls-and-sms).

Want to start building your solution but not quite sure how to get
started? Please feel free to let us know at support@messagebird.com,
we'd love to help!