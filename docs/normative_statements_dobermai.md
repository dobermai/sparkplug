### Sparkplug Architecture

|MUST/MAY|Statement | Page
|--------|----------| ----|
|MUST| At least one MQTT server MUST be part of the Sparkplug infrastructure
|MAY| There MAY be more than one MQTT server in the Sparkplug infrastructure
|MUST| THE MQTT server MUST be compliant with MQTT 3.1.1
|MUST | There MUST be only one Primay SCADA/IIoT Host
|MUST| There MAY be one or more secondary SCADA/IIoT Hosts


### Sparkplug Topic Namespace

|MUST/MAY/NN|Statement | Page
|--------|----------| ------ |
|MUST| The Sparkplug Topic Namespace MUST be encoded in UTF-8
|MUST| The Sparkplug Topic Namespace MUST have the structure namespace/group_id/message_type/edge_node_id/device_id
|MUST| The Sparkplug Topic Namespace elements MUST not use the characters "/", "#" and "+"
|MUST| The Sparklug Namespace MUST be SpBv1.0
|MUST| The message_Type element MUST be one of the following elements: NBIRTH, NDEATH, DBIRTH, DDEATH, NDATA, DDATA, NCMD, DCMD, STATE|
|MUST| The group_id combined with the edge-node_id MUST be unique in the same infrastructure
|NN| "Examples of where the group_id might be used include Gas/Oil...." |p12
|NN| The edge_node_id travels with every message published and should be as short as possible |13
|MUST| The device_id MUST be unique for the same edge_node_id.
|CAN| The device_id CAN be reused with other edge_node_id s.


### Sparkplug Messages

#### EoN

|MUST/MAY/NN|Statement | Page
|--------|----------| ------ |
|MUST| A EoN MUST publish a birth message to the MQTT server upon successful connection establishtment
|MUST NOT| A EoN MUST NOT publish any MQTT message before a birth message was sent and acknowledged
|MUST| A EoN MUST set a LWT message with the MQTT CONNECT packet with a valid death message
|NN | The Death message mechanism uses the LWT mechanism of the underlying MQTT transport| p14
|MAY| The MQTT server MAY modify the timestamp in the LWT death message upon delivery to the current timestamp observed on the server
