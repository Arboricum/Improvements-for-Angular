# Improvements-for-Angular
Proposal for a framework.json file in Angular applications

It is really hard sometime to figure out all the relations between angular components, expecially when they become many.
You'd want to know with a first glance who's child of who, or parents of who, or where a component is being used.
Maybe you'd wish to know which service or directive is being shared.
I found nothing on the web helping with this problem.
So I figured out a framework file where the app framework is actually displayed.
This will be a JSON file, with the following features:

- Camel case string -> components' class name
- Camel case string properties key-value -> it's for component, it's an object where the properties are:
    - @string (see below), in the following order: modules (@Mod), services (@Ser), directives (@Dir);
    - camel case strings for children components' class names;
    - the object will be an empty one if there are no children or @string.
- Camel case @string -> services (@Ser), directives (@Dir), modules (@Mod)
- @string properties key-value -> 
    - @Ser is an array of services, elements are the services' class names (camel case);
    - @Dir is an array of directives, elements are the directives' class names (camel case);
    - @Mod is an array of modules, elements are the modules' selector names (exact match).
- same indentation -> siblings
- different indentation -> lower is child of higher parent
- first level: only parents (only children of <app-root> or of <router-outlet>)

See an instance of a simple example app in the file framework.json.

It good be a best practice to provide the app with such a file, which I would nest inside the app folder.
Suggestions and comments are welcome.

