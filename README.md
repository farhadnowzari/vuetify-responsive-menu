# Vuetify responsive menu
Has it ever happened that you need some of your menus to open as a popup on mobile? If so, you must put your data one into the menu and one into the popup and do a `v-if` to switch and your data code weather it is in two separate files or in one file, it will be duplicates. With `vuetify-responsive-menu` we are going to have a menu which can be switched automatically from `Menu` to `Dialog` and your code will not be duplicated.

**Note:** This component is using `vuetify` and there are still more to be done on it but for a start it should just work perfectly.

# Installation
Install the package from npm
```
npm install vuetify-responsive-menu
```

# Usage
You can instsall it with `Vue.use` like below:
```
//main.js or vuetifu.js
import VResponsiveMenu from 'vuetify-responsive-menu';

Vue.use(VResponsiveMenu);
```
**OR** just import inside one componenet you want to use it in and add it to the `components` option.
```
//YourComponent.vue
import VResponsiveMenu from 'vuetify-responsive-menu';

export default({
    components: {
        VResponsiveMenu
    }
})
```

## Slots
* **activator:** By adding your component to this style the `responsive-menu` will automatically becomes visible on clicking on that `activator` control.
* **default:** This slot will hold the content of your menu to be shown inside a `Menu` or a `Dialog`.

## Properties
You can modify the properties of the `Menu` and `Dialog` from this component just how they are with normal Menu and normal Dialog.

**Note:** if you want to modify the dialog properties you need to start the name of that property with `dialog-` and the same applies on **Menu**. Look at the below example.
```
//YourComponent.vue
//For example you want to give a fullscreen to your dialog and offset-y to your menu.
<v-responsive-menu
    dialog-fullscreen
    menu-offset-y></v-responsive-menu>
```
Now here goes some other properties which are important.
* **switchBreakpoint:** If this is true the component will switch from menu to dialog, you can put a `$vuetify.breakpoint` here as value.
* **returnValue:** This can be anything and it support `sync`. This is incase you want one specific value be returned to you by clicking on a button in dialog.

## Methods
There are three accessible methods,

1. Close, which basically will close the component
2. Open, will open the component
3. Save, will call `this.$emit('update:returnValue', this.returnValue)` to update your value.


Let me know if anything is wrong so we can improve it.

