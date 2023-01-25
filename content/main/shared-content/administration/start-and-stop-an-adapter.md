---
uid: StartAndStopAnAdapter
---

# Start and stop an adapter

Complete the procedure appropriate for your operating system to start or stop an adapter service:

## Windows

1. Open Windows services.

1. Select **AVEVA Adapter for \<AdapterName\>**.

1. Select **Stop** to stop your adapter or select **Start** to start your adapter.

## Linux

1. Open command line.

1. Confirm the status of your adapter, then run one of the following:

 To **Start** AVEVA Adapter for \<AdapterName\>:

    ```cmdline
    sudo systemctl start pi.adapter.<adapterName>
    ```

 To **Stop** AVEVA Adapter for \<AdapterName\>:
  
      ```cmdline
      sudo systemctl stop pi.adapter.<adapterName>
      ```
  
1. Press Enter.
