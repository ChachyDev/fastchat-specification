# message
## Background
Messaging is a core part of `fastchat`. It allows for others to securely communicate with others
via the internet with a universal specification that anyone is free to implement.

## Specification

### PrivateMessageSendPacket/PrivateMessageReceivedPacket
| index | name      | type   | description                                                                       |
|-------|-----------|--------|-----------------------------------------------------------------------------------|
| 0     | id (0x1)      | int    | The ID of the packet sent. This is used for identification by the implementation. |
| 1     | user_id   | long   | The ID of the user who had sent the message.                                      |
| 2     | recipient | long   | The ID of the user who should receive the message.                                |
| 3     | content   | byte[] | The content of the message sent.                                                 |
#### Note
This specification is subject to change and breaking changes WILL come.
Support for attachments and such will be implemented.

Developers must choose how they want to deal with ID -> "Nicknames". The implementation
of the server can create a database to map IDs to "Nicknames" requested by the client.


### PrivateMessageAttachmentPacket/PrivateMessageAttachmentReceivePacket
| index | name       | type   | description                                                                                                                                                                                            |
|-------|------------|--------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0     | id (0x2)   | int    | The ID of the packet sent. This is used for identification by the implementation.                                                                                                                      |
| 1     | user_id    | long   | The ID of the user who had sent the message.                                                                                                                                                           |
| 2     | recipient  | long   | The ID of the user who should receive the message.                                                                                                                                                     |
| 3     | attachment | byte[] | Byte array of the attachment data. This could be a URL or actual file data. The server should take the data and choose itself whether it should process it as a URL or should leave it for image data. |
