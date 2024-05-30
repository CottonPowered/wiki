# PlayerPreLoginEvent

Triggers before the player fully logs in

| Method                   | Description                                     | Returns           |
| ------------------------ | ----------------------------------------------- | ----------------- |
| getPlayerUUID()          | Returns the player's UUID                       | UUID              |
| getPlayerName()          | Returns the player's name                       | String            |
| cancelConnection(String) | Cancels the connection with a reason            | void              |
| isConnectionCancelled()  | Whether the connection has been cancelled       | Boolean           |
| getCancelReason()        | Returns the reason the connection was cancelled | (Nullable) String |
