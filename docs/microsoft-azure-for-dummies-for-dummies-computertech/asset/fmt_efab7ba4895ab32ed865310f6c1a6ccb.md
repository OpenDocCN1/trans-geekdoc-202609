
## Azure Function App Components

*   A single **Function App (A)** contains one or more Functions.
*   Each Function that runs in the Function App's run space is stored here **(B)**.
*   A **Function Proxy (C)** allows you to present a single API endpoint for all Functions in a single Function app to other Azure or non-Azure API services.
*   **Function Apps** support **deployment slots (D)**; they serve the same purpose as deployment slots for App Service web apps, and they support slot swapping.
*   **Function App Settings (E)** is where you specify settings for a Function App, Function, or Proxy, depending on the context.

## Prerequisites: Creating the Images Blob Container

Before you create the function, you should create the `images` blob container you'll need for this website-upload example. If you have **Azure Storage Explorer** installed, proceed! If not, refer to [Chapter 3](#c03.xhtml) for details on installing it.

![FIGURE 8-4: Whoever designed the Function App's user interface wasn't paying attention to how the rest of the Azure portal behaves.](images/9781119612148-fg0804.png)

**[FIGURE 8-4:](#c08.xhtml#rc08-fig-0004)** Whoever designed the Function App's user interface wasn't paying attention to how the rest of the Azure portal behaves.

![Remember](images/remember.png) **Azure Storage Explorer** is a free, cross-platform desktop application that makes working with Azure storage accounts a snap. Obtain the tool at [`https://azure.microsoft.com/en-us/features/storage-explorer/`](https://azure.microsoft.com/en-us/features/storage-explorer/).

Follow these steps to create a blob container for the new Function:

1.  **Open Azure Storage Explorer, and authenticate to your Azure subscription.**
2.  **Expand the storage account you created for your Function App, right-click Blob Containers, and choose Create Blob Container from the shortcut menu.**
    Azure creates the container and places your cursor next to it, all ready for you to name the new object.
3.  **Name the container `images`, and press Enter to confirm.**

## Creating the Function

Excellent. You're almost finished. Now you need to create a function. Follow these steps:

1.  **Open your Function App in the Azure portal.**
2.  **In the Functions row, click the plus sign.**
    The details pane on the right leads you through a Function Wizard, the first step of which is choosing a development environment.
3.  **Choose In-Portal as your development environment, and click Continue.**
    Both Visual Studio and Visual Studio Code have native support for writing Functions.
4.  **In the Create a Function pane, click More Templates, and click Finish and view templates.**
    I show you this in [Figure 8-5](#c08.xhtml#c08-fig-0005).

    ![FIGURE 8-5: Creating a Function inside the Azure portal.](images/9781119612148-fg0805.png)

    **[FIGURE 8-5:](#c08.xhtml#rc08-fig-0005)** Creating a Function inside the Azure portal.
5.  **Click View Templates to view the Azure Function trigger gallery.**
6.  **In the gallery, select the Azure Blob Storage trigger.**
    You'll probably be prompted to install the Azure Storage extension; click Install, and let the process complete.
7.  **Complete the New Function blade.**
    Complete the following fields:
    *   **Name:** I called mine `BlobUploadFx`. This is the name of the Function that will be contained inside the Function App. The name should be short and descriptive.
    *   **Azure Blob Storage Trigger Path:** This setting is important. You want to leave the `{name}` bit alone because it's a variable that represents any uploaded blob. The path should look like this:
        `images/{name}`
    *   **Storage Account Connection:** Click New, and select your Function's storage account.
8.  **Click Create when you're finished.**

When you select your function on the Function App's left menu, you can see your starter C# source code. For this example, the code should look like this:

```csharp
public static void Run(Stream myBlob, string name, ILogger log)
{
    log.LogInformation($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
}
```

This code says "When the function is triggered, write the name and size of the blob to the console log." This example is simple so that you can focus on how Functions work instead of getting bogged down in programming-language semantics.

The new Function contains the following three settings blades:

*   **Integrate:** This blade is where you can edit your trigger, inputs, and outputs.
*   **Manage:** This blade is where you can disable, enable, or delete the Function, as well as define host keys that authorize API access to the Function.
*   **Monitor:** Here, you can view successful and failed Function executions and optionally access Application Insights telemetry from the Function.

## Testing

All you have to do to test your function is follow these steps:

1.  **In Azure Storage Explorer, upload an image file to the `images` container.**
    To do this, select the container and then click Upload from the Storage Explorer toolbar. You can upload individual files or entire folders.
    Technically, you can upload any file, image or otherwise, because all files are considered to be blobs.
2.  **In the Azure portal, select your Function App, switch to the Logs view, and watch the output.**
    [Figure 8-6](#c08.xhtml#c08-fig-0006) shows the output from a test.

![FIGURE 8-6: Our Azure Function in action.](images/9781119612148-fg0806.png)

**[FIGURE 8-6:](#c08.xhtml#rc08-fig-0006)** Our Azure Function in action.

## Configuring Function App Settings

Before I discuss Logic Apps, I want to make sure that you understand how to tweak Function App settings. You may want to switch from Consumption to App Service plan pricing, for example, or vice versa. Or maybe you want to test a different run-time environment.

I have a difficult time navigating the Function App configuration blades, mainly because they're completely different from the rest of the Azure portal UI. I also think there's some redundancy in the places where some settings controls are located. To make things easier, here's a summary of the major capabilities of each settings blade in the Function App:

![Remember](images/remember.png) You need to be at the Function App scope (above Functions in the navigation UI). You can see this convention in [Figure 8-7](#c08.xhtml#c08-fig-0007).

*   **Overview:** Use this blade to stop, start, and restart the Function App. You also can download all site content for use with a local integrated development environment.
*   **Platform Features:** This blade is where most Function App settings categories reside.
*   **Function App Settings:** From this blade, you can view usage quota and manage host keys.
*   **Configuration, Application Settings:** This blade is where you manage application key/value pair settings and database connection strings.
*   **Configuration, General Settings:** This blade is where you can configure Architecture; FTP state, HTTP version; Remote debugging.

![FIGURE 8-7: Understanding the relationship between the Function App and its enclosed Functions.](images/9781119612148-fg0807.png)

**[FIGURE 8-7:](#c08.xhtml#rc08-fig-0007)** Understanding the relationship between the Function App and its enclosed Functions.

## Building Workflows with Azure Logic Apps

Suppose that your company's marketing department wants to be notified any time a current or prospective customer mentions your corporate handle on Twitter. Without Logic Apps, your developers would have to register for a developer Twitter account and API key, after which they'd need to immerse themselves in the Twitter API to understand how to integrate Twitter with your corporate notification platform.

Instead, your developers can configure a Logic App to trigger on particular Twitter tweets and send an email message to an Outlook mailbox without knowing Twitter or Office 365 APIs. [Figure 8-8](#c08.xhtml#c08-fig-0008) shows a workflow for this Logic App.
