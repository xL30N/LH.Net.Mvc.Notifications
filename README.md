# MVC Notifications

The package consists of the following:

- Controller extension to add notifications
- Enum for the notification message type (success, error, information and warning)
- Tag helper to generate the HTML for the notification

## Controller Extension

Once the namespace has been added to the controller, the ShowNotification extension method can be called with the content and type.

```csharp
using LH.Net.Mvc.Notification
|
|...
|
this.ShowNotification("Success message", MessageType.Success);
```

The extension method adds the message to TempData, allowing messages to persist to the next request or after a redirect. 

The message type defines the CSS classes that are assigned to the output, allowing for them to be styled accordingly. These styles also match Bootstrap alert styles, so no further styling is required when used with Bootstrap 3+.

## Tag helper

In order to display the notification set via the controller extension, the taghelper assembly must be added to the _viewimports.cshtml files and the notification tag positioned in the view.

The following will load any tag helpers found within the assembly LH.Net.Mvc.Notification.

```csharp
@addTagHelper *, LH.Net.Mvc.Notification
```

This notification can be added to any view, although by placing it within _layout.cshtml it will provide a consistent place for notifications.

```csharp
<notification></notification>
```