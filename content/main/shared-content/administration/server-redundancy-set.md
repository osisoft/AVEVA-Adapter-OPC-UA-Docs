---
uid: RetrieveRedundancySet
---

# Retrieve Redundant Server Set

The AVEVA OPC UA Adapter provides a rest endpoint for querying the current redundant server set the adapter is using for server failover.

Complete the following steps to retrieve the redundant server set of an AVEVA OPC UA Adapter:

1. Use any of the [Configuration tools](xref:ConfigurationTools) capable of making HTTP requests.
2. Run a `GET` command to the following endpoint: `http://localhost:5590/api/v1/configuration/<ComponentId>/RedundantServerSet`

   **Note:** `5590` is the default port number. If you selected a different port number, replace it with that value.

   Example using `curl`:

   **Get redundant server set for adapter hosted on port 5590**

   ```bash
   curl -X GET "http://localhost:5590/api/v1/configuration/<ComponentId>/RedundantServerSet"
   ```

   Example result:

    ```json
    {
        "ServerAddresses": [
            "opc.tcp://Server1",
            "opc.tcp://Server2"
        ]
    }
    ```