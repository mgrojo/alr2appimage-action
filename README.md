# alr2appimage-action
Reusable action that will build a Linux package ([AppImage](https://appimage.org/), Deb, RPM) 
from your [Alire](https://alire.ada.dev/) crate and publish it to your releases section.

# Examples

Add this to your GitHub Action.

Example with all the arguments, which are optional. The indicated values are the default ones.

```yaml
    name: Continuous AppImage
    runs-on: ubuntu-22.04
    steps:
       - name: Checkout
         uses: actions/checkout@v2
       - name: alr2appimage-action
         uses: mgrojo/alr2appimage-action@v1
         with:
           alireVersion: 2.1.0 # Use custom version of Alire
           alr2appimageVersion: 1.1.1 # Use custom version of alr2appimage.
           alr2appimageArgs: "--use-version" # Arguments to pass to alr2appimage
           tagName: "continuous" # Tag to use for your application release.
           crateDir: "." # Directory where your Alire crate is located
           deleteExistent: false # Delete the tag and release if already existent
```

Example to make a continuous release with AppImage, Deb and RPM packages.

```yaml
    name: Continuous Packages
    runs-on: ubuntu-22.04
    steps:
       - name: Checkout
         uses: actions/checkout@v2
       - name: alr2appimage-action
         uses: mgrojo/alr2appimage-action@v1
         with:
           alr2appimageArgs: "-o appimage,deb,rpm --use-version" # Arguments to pass to alr2appimage
           tagName: "continuous" # Tag to use for your application release.
           deleteExistent: true # Delete the tag and release if already existent
```

Real examples in:
* https://github.com/mgrojo/open_url/blob/main/.github/workflows/main.yml
* https://github.com/LionelDraghi/bbt/blob/main/.github/workflows/appimage.yml
