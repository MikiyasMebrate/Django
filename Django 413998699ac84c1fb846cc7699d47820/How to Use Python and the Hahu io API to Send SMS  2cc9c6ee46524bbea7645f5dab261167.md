# How to Use Python and the Hahu.io API to Send SMS Messages

![https://assets.cdn.prod.twilio.com/images/outgoing-sms.width-800.png](https://assets.cdn.prod.twilio.com/images/outgoing-sms.width-800.png)

If you're looking for a way to automate the process of sending SMS messages using your [Hahu.io](http://hahu.io/) account, Python and the [Hahu.io](http://hahu.io/) API can help. In this tutorial, we'll show you how to use Python and the [Hahu.io](http://hahu.io/) API to send an SMS message.

### Prerequisites

Before we get started, you'll need to have the following:

- A [Hahu.io](http://hahu.io/) account
- Your [Hahu.io](http://hahu.io/) API secret (you can find this on the Tools -> API Keys page)
- Python 3.x installed on your computer
- The requests library installed (you can install this using pip)

### Getting Started

To get started, open up a new Python file and import the requests library:

```python
import requests
```

Next, you'll need to define your API secret and the message information that you want to send. Replace `API_SECRET` with your actual API secret, and update the `device`, `sim`, `priority`, `phone`, and `message` fields with the appropriate values:

```
apiSecret = "API_SECRET"

message = {
    "secret": apiSecret,
    "mode": "devices",
    "device": "00000000-0000-0000-d57d-f30cb6a89289",
    "sim": 1,
    "priority": 1,
    "phone": "+251123456789",
    "message": "Hello World!"
}

```

### Sending the Request

Now that you have your API secret and message information defined, you can send a POST request to the [Hahu.io](http://hahu.io/) API using the `requests.post()` function:

```
r = requests.post(url = "<https://hahu.io/api/send/sms>", params = message)

```

This will send a request to the [Hahu.io](http://hahu.io/) API with the message information you defined in the `message` dictionary. The response from the API will be stored in the `r` variable.

### Handling the Response

Finally, you can handle the response from the API by converting it to a JSON object:

```
result = r.json()

```

You can then do something with the `result` object, such as print it to the console or write it to a file.

### Conclusion

In this tutorial, we showed you how to use Python and the [Hahu.io](http://hahu.io/) API to send an SMS message. With this knowledge, you can now automate the process of sending SMS messages using Python and your [Hahu.io](http://hahu.io/) account.