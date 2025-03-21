# alr2appimage-action
Reusable action that you can use to build an [AppImage](https://appimage.org/) 
from your [Alire](https://alire.ada.dev/) crate and publish it to your releases section.

# Example

Add this to your GitHub Action.
Full example in https://github.com/mgrojo/open_url/blob/main/.github/workflows/main.yml

```yaml
    name: Continuous AppImage
    runs-on: ubuntu-20.04
    steps:
       - name: Checkout
         uses: actions/checkout@v2
       - name: alr2appimage-action
         uses: mgrojo/alr2appimage-action@v1
         with: # All these arguments are optional. These are the default values.
           alr2appimageVersion: 1.0.0 # Use custom version of alr2appimage.
           alr2appimageArgs: "--use-version" # Arguments to pass to alr2appimage
           tagName: "continuous" # Tag to use for your application release.
           crateDir: "." # Directory where your Alire crate is located
```
