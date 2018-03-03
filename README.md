[{"id":"e6299896.de5358","type":"comment","z":"98b01922.5cc178","name":"url","info":"http://localhost:1880/hello?topic=devices/garage/tor\nhttp://192.168.0.6:1880/zway/garage","x":90,"y":40,"wires":[]},{"id":"7224c7cc.e122f","type":"mqtt in","z":"98b01922.5cc178","name":"","topic":"zway/garage","qos":"0","broker":"2d3724b2.56ba64","x":110,"y":120,"wires":[["cbf594db.2475"]]},{"id":"588c3185.821588","type":"debug","z":"98b01922.5cc178","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"payload","x":530,"y":40,"wires":[]},{"id":"cbf594db.2475","type":"change","z":"98b01922.5cc178","name":"Store sensor","rules":[{"t":"set","p":"payload","pt":"flow","to":"payload","tot":"msg"}],"action":"","property":"","from":"","to":"","reg":false,"x":290,"y":120,"wires":[["588c3185.821588","5a6c9f57.7511f"]]},{"id":"37e1cfa1.b7b0d","type":"http in","z":"98b01922.5cc178","name":"","url":"/zway/garage","method":"get","upload":false,"swaggerDoc":"","x":130,"y":420,"wires":[["dad48ebf.3aa0c8"]]},{"id":"dad48ebf.3aa0c8","type":"change","z":"98b01922.5cc178","name":"Copy sensor","rules":[{"t":"set","p":"payload","pt":"msg","to":"payload","tot":"flow"}],"action":"","property":"","from":"","to":"","reg":false,"x":330,"y":420,"wires":[["8511a7ac.1d3ec8","958bae0c.82cf2"]]},{"id":"958bae0c.82cf2","type":"http response","z":"98b01922.5cc178","name":"","x":510,"y":420,"wires":[]},{"id":"1ccbc429.787c94","type":"http request","z":"98b01922.5cc178","name":"Garage","method":"GET","ret":"txt","url":"http://things.ubidots.com/api/v1.6/devices/garage/tor/lv?token=A1E-CslQb5aNpczt85wsxDlcF8KXZ7x9us","tls":"","x":100,"y":500,"wires":[[]]},{"id":"69ed23a5.c7b74c","type":"inject","z":"98b01922.5cc178","name":"","topic":"","payload":"{\"tor\": [{\"value\": 0.00}], \"lux\": [{\"value\": 103.00}]}","payloadType":"str","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":90,"y":200,"wires":[["5d26ad92.c0d5f4"]]},{"id":"299cfa1f.427586","type":"inject","z":"98b01922.5cc178","name":"","topic":"","payload":"{\"tor\": [{\"value\": 1.00}], \"lux\": [{\"value\": 103.00}]}","payloadType":"str","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":90,"y":280,"wires":[["5d26ad92.c0d5f4"]]},{"id":"5d26ad92.c0d5f4","type":"mqtt out","z":"98b01922.5cc178","name":"","topic":"zway/garage","qos":"","retain":"true","broker":"2d3724b2.56ba64","x":290,"y":240,"wires":[]},{"id":"24b3efb1.629a78","type":"e-mail","z":"98b01922.5cc178","server":"smtp.strato.de","port":"465","secure":true,"name":"fred@lupper.de","dname":"Mail","x":910,"y":120,"wires":[]},{"id":"81352ae4.a92b08","type":"change","z":"98b01922.5cc178","name":"","rules":[{"t":"set","p":"topic","pt":"msg","to":"Garage zu","tot":"str"}],"action":"","property":"","from":"","to":"","reg":false,"x":710,"y":80,"wires":[["24b3efb1.629a78"]]},{"id":"8511a7ac.1d3ec8","type":"debug","z":"98b01922.5cc178","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"false","x":530,"y":340,"wires":[]},{"id":"5a6c9f57.7511f","type":"switch","z":"98b01922.5cc178","name":"","property":"payload","propertyType":"msg","rules":[{"t":"cont","v":"{\"value\": 0.00}","vt":"str"},{"t":"cont","v":"{\"value\": 1.00}","vt":"str"}],"checkall":"true","repair":false,"outputs":2,"x":510,"y":120,"wires":[["81352ae4.a92b08"],["41e15c20.30da6c"]]},{"id":"41e15c20.30da6c","type":"change","z":"98b01922.5cc178","name":"","rules":[{"t":"set","p":"topic","pt":"msg","to":"Garage offen","tot":"str"}],"action":"","property":"","from":"","to":"","reg":false,"x":710,"y":160,"wires":[["24b3efb1.629a78"]]},{"id":"2d3724b2.56ba64","type":"mqtt-broker","z":"","name":"Home","broker":"localhost","port":"1883","clientid":"","usetls":false,"compatmode":true,"keepalive":"60","cleansession":true,"willTopic":"","willQos":"0","willPayload":"","birthTopic":"","birthQos":"0","birthPayload":""}]
