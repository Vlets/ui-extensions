# Unsplash UI Extension for Bloomreach Experience

This UI Extension integrates Bloomreach Experience with Unsplash, a source of freely useable stock images. It leverages the official Unsplash API to browse images and use these within Bloomreach powered sites.

## How does the UI Extension work?

From a Bloomreach document, a picker dialog can be opened that interacts with Unsplash. The initial view shows random images, and a query can be executed to search images for a certain topic. Searches can be filtered for landscape, portrait or square images. After selecting an image, a reference data object is stored in the Bloomreach document. Sites can then use these references to add the selected image to a page.

## Requirements

- A Bloomreach Experience Manager (brXM) project running on version 13.2.0 or above.
- An account with Unsplash, in which an app with Access key has been created.

## Use the Unsplash UI Extension in your brXM project

### Step 1: Configure the extension in brXM

Open the console of your brXM instance and browse to the node `/hippo:configuration/hippo:frontend/cms/ui-extensions`. Then import the following YAML snippet:

```yaml
/Unsplash:
  jcr:primaryType: frontend:uiExtension
  frontend:config: '{"clientID":"YOUR_ACCESS_KEY_HERE", "unsplashRandomUrl":"https://api.unsplash.com/photos/random","unsplashSearchUrl":"https://api.unsplash.com/search/photos"}'
  frontend:displayName: Unsplash
  frontend:extensionPoint: document.field
  frontend:url: https://bloomreach.github.io/ui-extensions/samples/unsplash/
```

The `frontend:config` property holds a JSON object that controls the behavior of the Unsplash extension. The following properties can be used:

| Property name | Description | Remarks |
|---------------|-------------|---------|
| `clientID` | To use the Unsplash API, you first have to register for an account, set up an app, and obtain an access key. This key will be used in the extension. More details can be found [here](https://unsplash.com/documentation#getting-started).| mandatory |
| `unsplashRandomUrl` | This property holds the base url for requesting random images from Unsplash. If this property is omitted, a hardcoded value is used. | optional |
| `unsplashSearchUrl` | This property holds the base url for searching images from Unsplash. If this property is omitted, a hardcoded value is used. | optional |

### Step 2: Add a Unsplash field to your document type(s)

Using the document type editor, add an "Open UI String" field to the relevant document type(s). Change the 'path' and 'Default Caption' to values that make sense for your project and set 'ui.extension' to 'unsplash' (this needs to match the name of the node created in the previous step).

If your project uses dynamic content beans (default since 13.2.0), the Unsplash field will be available for use in frontend templates immediately. If your project does not use dynamic content beans, you will need to update the content bean(s) of the changed document type(s). When using [Essentials](https://documentation.bloomreach.com/library/setup/introduction.html), this can be done using the [Bean Writer tool](https://documentation.bloomreach.com/library/setup/development-tools.html#beanwriter).

You can now start using the plugin in your documents.

### Step 3: Render the image in your frontend template(s)

You can now start using the Unsplash image object reference that is stored in your document to render the image in your frontend template(s). More details about the different image variants and how to manipulate the image can be found [here](https://unsplash.com/documentation#dynamically-resizable-images).

## Resources

- [Bloomreach UI Extensions Documentation](https://documentation.bloomreach.com/library/concepts/open-ui/introduction.html)
- [Unsplash Developer documentation](https://unsplash.com/developers)
- [Unsplash Homepage](https://unsplash.com/)