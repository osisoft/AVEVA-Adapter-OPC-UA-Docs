---
uid: StartAndStopAnAdapter
---

# Start and stop an adapter

Complete the procedure appropriate for your operating system to start or stop an adapter service:

## Windows

1. Open Windows services.

2. Select **[!include[product-name](../_includes/inline/product-name.md)]**.

3. Depending on whether your adapter is running or not, click either **Start** or **Stop**.

## Linux

1. Open command line.

2. Depending on whether your adapter is running or not, type one of the following commands:

    Example:

    _Start_ [!include[product-name](../_includes/inline/product-name.md)]

    ```cmdline
    sudo systemctl start aveva.adapter.opcua
    ```

    Example:

    _Stop_ [!include[product-name](../_includes/inline/product-name.md)]
  
      ```cmdline
      sudo systemctl stop aveva.adapter.opcua
      ```
  
3. Press Enter.
