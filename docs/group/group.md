# group
## Background
In the fastchat specification "groups" are entities containing multiple recipients.

## Specification

### GroupMessageSendPacket/GroupMessageSentPacket
#### Type: C -> S / S -> C
| index | name     | type   | description                                                                                                                                                                                                |
|-------|----------|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0     | id (0x3) | int    | The ID of the packet sent. This is used for identification by the implementation.                                                                                                                          |
| 1     | group_id | long   | Group IDs are the core bases of groups. They should be ALWAYS be unique as they will be used to retrieve groups and their data                                                                             |
| 2     | content  | byte[] | Byte array of the content sent. This would normally be just UTF-8 data unless the client has (purposely ?) sent invalid data. In such case simply discard the processing of the packet for safety reasons. |

### GroupJoinRequestPacket
#### Type: C -> S
| index | name      | type | description                                                                                                                    |
|-------|-----------|------|--------------------------------------------------------------------------------------------------------------------------------|
| 0     | id (0x4)  | int  | The ID of the packet sent. This is used for identification by the implementation.                                              |
| 1     | group_id  | long | Group IDs are the core bases of groups. They should be ALWAYS be unique as they will be used to retrieve groups and their data |
| 2     | joiner_id | long | The ID of the user requesting to join.                                                                                         |

### GroupJoinResponsePacket
#### Type: S -> C
| index | name      | type   | description                                                                                                                    |
|-------|-----------|--------|--------------------------------------------------------------------------------------------------------------------------------|
| 0     | id (0x5)  | int    | The ID of the packet sent. This is used for identification by the implementation.                                              |
| 1     | group_id  | long   | Group IDs are the core bases of groups. They should be ALWAYS be unique as they will be used to retrieve groups and their data |
| 2     | joiner_id | long   | The ID of the user requesting to join.                                                                                         |
| 3     | allowed   | int    | If they were allowed in then 1 and if not 0.                                                                                   |
| 4     | reason    | byte[] | Reason that the user was denied from joining the group. (Could be lack of permissions, etc.)                                   |