Sometimes, you may want to allow the user to save preferences, like the default state of a button of the default view. This is done through the preferences modules.

``` typesccript
import { Me } from ‘entcore’;

const appPreferences = await Me.preference('myapp');
console.log(Me.preferences.myapp.buttonToggled);
Me.preferences.myapp.buttonToggled = false;
Me.savePreference('myapp');
```
