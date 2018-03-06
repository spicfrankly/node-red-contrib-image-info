# node-red-contrib-image-info
A Node Red node to get information about an image

## Install
Run the following npm command in your Node-RED user directory (typically ~/.node-red):
```
npm install node-red-contrib-image-info
```
## Usage
This node can be used to get the following information about the image, arriving in the input `msg.payload`:
+ ***Format***: the format of the image in pixels.
+ ***Width***: the width of the image in pixels.
+ ***Height***: the height of the image in pixels.

![Flow](https://raw.githubusercontent.com/bartbutenaers/node-red-contrib-image-info/master/images/info_flow.png)
```
[{"id":"e63f49ee.566408","type":"image-information","z":"47b91ceb.38a754","name":"","x":1290,"y":460,"wires":[[]]},{"id":"b40ce94f.94d888","type":"http request","z":"47b91ceb.38a754","name":"","method":"GET","ret":"bin","url":"","tls":"","x":1100,"y":460,"wires":[["e63f49ee.566408"]]},{"id":"43ad92cb.8cc7ec","type":"inject","z":"47b91ceb.38a754","name":"Png 640x480","topic":"","payload":"https://dummyimage.com/640x480.png&text=png+of+640+x+480","payloadType":"str","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":710,"y":420,"wires":[["3a8476de.7d91aa"]]},{"id":"3a8476de.7d91aa","type":"change","z":"47b91ceb.38a754","name":"","rules":[{"t":"set","p":"url","pt":"msg","to":"payload","tot":"msg"}],"action":"","property":"","from":"","to":"","reg":false,"x":910,"y":460,"wires":[["b40ce94f.94d888"]]},{"id":"65e09b54.00b1f4","type":"inject","z":"47b91ceb.38a754","name":"Jpg 320x240","topic":"","payload":"https://dummyimage.com/320x240.jpg&text=jpg+of+320+x+240","payloadType":"str","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":710,"y":460,"wires":[["3a8476de.7d91aa"]]},{"id":"975f5022.973f6","type":"inject","z":"47b91ceb.38a754","name":"Gif 1280x960","topic":"","payload":"https://dummyimage.com/1280x960.gif&text=gif+of+1280+x+960","payloadType":"str","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":710,"y":500,"wires":[["3a8476de.7d91aa"]]}]
```

This node is based on the [image-size](https://www.npmjs.com/package/image-size) library, where you can find a list of all allowed image formats.

## Output message
The information will be displayed in the node status, but the same information will be added to the input message:
+ ***Format***: the format will be stored in the output `msg.format`.
+ ***Width***: the width will be stored in the output `msg.width`.
+ ***Height***: the heigth will be stored in the output `msg.heigth`.
