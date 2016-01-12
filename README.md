# esp8266-send-thingspeak
easily send/read data to/from thingspeak

example for sending data:

```
sendToTS = require("sendToTS")
sendToTS.setKey('YOUR_API_WRITE_KEY')
valSet = sendToTS.setValue(1,12) -- channel, data.  sendToTS returns a boolean, true if set successfully
sendToTS.sendData(true, 'callbackfile.lua') -- show debug msgs, optional callback file (can omit this argument)
sendToTS = nil
package.loaded["sendToTS"]=nil -- these last two lines help free up memory
```

reading data is not so easy as of now.
Example:

```
fields = {}
createdTimes = {}
readTS = require("readTS")
readTS.setChannelID("yourChID")
readTS.setKey("your read API key")
readTS.readData(true, 1, 'callbackFile.lua') -- args: filename containing writekey, readkey on two separate lines; show debug msg = true; number of results to return; optional callback file to run after completed request
readTS = nil
package.loaded["readTS"]=nil
print(fields[1])
```
