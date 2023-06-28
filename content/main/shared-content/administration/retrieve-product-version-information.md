---
uid: RetrieveProductVersionInformation
---

# Retrieve product version information

The product version information includes the adapter framework version, application version, the version of the underlying .NET Core framework, and the operating system that the adapter is running on.

Complete the following steps to retrieve the product version information of an AVEVA adapter:

1. Use any of the [Configuration tools](xref:ConfigurationTools) capable of making HTTP requests.
2. Run a `GET` command to the following endpoint: `http://localhost:5590/api/v1/Diagnostics/ProductInformation`

   **Note:** `5590` is the default port number. If you selected a different port number, replace it with that value.

   Example using `curl`:

   **Get product information for adapter hosted on port 5590**

   ```bash
   curl -X GET "http://localhost:5590/api/v1/Diagnostics/ProductInformation"
   ```

   Example result:

    ```code
    {
      "Product Name": "AVEVA Adapter for OpcUa",
      "Product Version": "1.4.0.196",
      "Adapter Framework Version": "1.7.0.109",
      "Runtime Version": ".NET 6.0.14",
      "Operating System": "Microsoft Windows 10.0.19045"
    }
    ```
