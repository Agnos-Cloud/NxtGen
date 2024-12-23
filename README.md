# NxtGen
Bootstrap NextJs apps

## Creating an App

It should be possible to create an app from a template.

```bash
nextgen create app my-app --template=hospital-management-system
```

It should be possible to specify a color scheme

```bash
nextgen create app my-app --template=hospital-management-system --scheme=metallic-gray
```

It should be possible to specify a default layout for the app

```bash
nextgen create app my-app --template=hospital-management-system --layout=navbar-only
```

It should be possible to specify features that must be present in the app

```bash
nextgen create app my-app --template=hospital-management-system --features=notifications,light-dark-mode,authentication
```

## App templates

## Color Scheme

We can have CSS class names in the form of `navbar-bg`, `navbar-color`, `page-bg`, `page-color`, `footer-bg`, `footer-color`, etc.

This way, a color scheme boils down to providing values for these class names.

A color scheme may come in the following modes: light, dark, and system.

It should be possible to add a color scheme.

```bash
nextgen add scheme metallic-gray
```

It should be possible to set a color scheme as the current scheme.

```bash
nextgen use scheme metallic-gray
```

It should be possible to remove a color scheme

```bash
nextgen remove scheme metallic-gray
```

The system should handle the case where the current scheme is removed.

It should be possible to set the value of a specific color in the current color scheme.

```bash
nextgen set color --name=navbar-bg --value=green
```

It should be possible to set the value of a specific color in a specified color scheme.

```bash
nextgen set color --name=navbar-bg --value=green --scheme=metallic-gray
```

It should be possible to add and remove colors.

## Theme

We can go beyond color schemes and also handle other UI/UX areas like typography, iconography, etc.

## Layouts

To use a layout for the app:

```bash
nextgen use layout --name=navbar-and-sidebar
```

To use a layout for a page:

```bash
nextgen use layout --name=navbar-only --pages=privacy,terms,settings
```

## Pages

To add a page:

```bash
nextgen add page --name=settings --path="/settings" --template=simple-settings-page
```

To have the page designed by AI:

```bash
nextgen add page --name=privacy --path="/privacy" --prompt="A simple privacy policy page for a hospital management system"
```

It should be possible to delete a page

## Features

A feature is a collection of codes (components, context providers, hooks, etc.) that work together to provide a specific functionality/capability.

#### Implementation Details

A feature will be installed into a folder named after the feature, inside the `features` folder.

The system will keep track of all npm packages installed by a feature. (Maybe all other constructs, i.e. pages, themes, schemes, layouts, etc, should also be allowed to install npm packages.)
When uninstalling a feature, it's npm packages (as long as they were directly installed by the feature and are not being used by any other feature/construct) will also be uninstalled.

## Module

A module allows us to package constructs (features, pages, layouts, etc) that ought to be installed and uninstalled together.

## useApp

There will be a special hook, say `useApp`, that will provide functions for handling schemes, themes, layouts, pages, features, etc. programmatically.

```js
import { useApp } from "...";
// ...
const { setLayout } = useApp();
// ...
setLayout("navbar-only");
```
