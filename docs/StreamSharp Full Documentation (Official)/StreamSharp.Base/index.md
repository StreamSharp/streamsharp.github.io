# StreamSharp Base

## What is StreamSharp Base?

StreamSharp base is the functionality that handles communication to and from the StreamDeck. It passes the JSON stuff as simple objects, and is dependent on you providing you interpreting the data. It also does not come with a graphics engine, and sends the image data as a simple `string base64encoded`.