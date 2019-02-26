This tab will (eventually) help you design a custom url for Venus which will do magical stuff. It will allow you to set settings, load scripts, and set up the environment however you want to. I am still working on this so there are not too many details about it.

* `target` with a url will load the contents of the url into the editor (Note that this feature relies on another website which bypasses CSRF because Venus would not be able to read the results of wherever the file is which you are trying to access.).
* `code` will load into the editor whatever it is set equal to.
* `override` will disable/enable the override prompt if you have save data in the editor on load with target or code set.
* `save` will set wether venus should save your data or not.
* `clear` if this is set to true, Venus will clear the LocalStorage and refresh.