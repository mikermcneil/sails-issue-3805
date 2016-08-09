# sails-issue-3805

See https://github.com/balderdashy/sails/issues/3805


Can't reproduce:

I tested with:

```
mongo-test@0.0.0 /Users/mikermcneil/code/sandbox/mongo-test
├── ejs@2.3.4 -> /Users/mikermcneil/code/sails/node_modules/ejs
├── grunt@1.0.1 -> /Users/mikermcneil/code/sails/node_modules/grunt
├── grunt-contrib-clean@1.0.0 -> /Users/mikermcneil/code/sails/node_modules/grunt-contrib-clean
├── grunt-contrib-coffee@1.0.0 -> /Users/mikermcneil/code/sails/node_modules/grunt-contrib-coffee
├── grunt-contrib-concat@1.0.1 -> /Users/mikermcneil/code/sails/node_modules/grunt-contrib-concat
├── grunt-contrib-copy@1.0.0 -> /Users/mikermcneil/code/sails/node_modules/grunt-contrib-copy
├── grunt-contrib-cssmin@1.0.1 -> /Users/mikermcneil/code/sails/node_modules/grunt-contrib-cssmin
├── grunt-contrib-jst@1.0.0 -> /Users/mikermcneil/code/sails/node_modules/grunt-contrib-jst
├── grunt-contrib-less@1.3.0 -> /Users/mikermcneil/code/sails/node_modules/grunt-contrib-less
├── grunt-contrib-uglify@1.0.1 -> /Users/mikermcneil/code/sails/node_modules/grunt-contrib-uglify
├── grunt-contrib-watch@1.0.0 -> /Users/mikermcneil/code/sails/node_modules/grunt-contrib-watch
├── grunt-sails-linker@0.10.1 -> /Users/mikermcneil/code/sails/node_modules/grunt-sails-linker
├── grunt-sync@0.5.2 -> /Users/mikermcneil/code/sails/node_modules/grunt-sync
├── include-all@0.1.6 -> /Users/mikermcneil/code/sails/node_modules/include-all
├── rc@1.0.1 -> /Users/mikermcneil/code/sails/node_modules/rc
├── sails@0.12.4 -> /Users/mikermcneil/code/sails
├── sails-disk@0.10.10 -> /Users/mikermcneil/code/sails/node_modules/sails-disk
└── sails-mongo@0.12.1
```


After seeding some data, and then using the REPL:
```
Gruntfile.js README.md    api          app.js       assets       config       node_modules package.json tasks        views
fatal: Not a git repository (or any of the parent directories): .git
mongo-test: ∑ sails lift

info: Starting app...

info: 
info:                .-..-.
info: 
info:    Sails              <|    .-..-.
info:    v0.12.4             |\
info:                       /|.\
info:                      / || \
info:                    ,'  |'  \
info:                 .-'.-==|/_--'
info:                 `--'-------' 
info:    __---___--___---___--___---___--___
info:  ____---___--___---___--___---___--___-__
info: 
info: Server lifted in `/Users/mikermcneil/code/sandbox/mongo-test`
info: To see your app, visit http://localhost:1337
info: To shut down Sails, press <CTRL> + C at any time.

debug: -------------------------------------------------------
debug: :: Tue Aug 09 2016 14:24:04 GMT-0500 (CDT)

debug: Environment : development
debug: Port        : 1337
debug: -------------------------------------------------------
^Cmongo-test: ∑ sails console

info: Starting app in interactive mode...

info: Welcome to the Sails console.
info: ( to exit, type <CTRL>+<C> )

sails> User.find({text: 'true'}).exec(console.log)
undefined
sails> null [ { name: 'brandise',
    text: 'true',
    createdAt: '2016-08-09T19:24:20.062Z',
    updatedAt: '2016-08-09T19:24:20.062Z',
    id: '57aa2de4289a5a3248416cef' } ]
```


I also saw the expected behavior when testing with blueprints; both with `http://localhost:1337/user/find?text=true` and with `http://localhost:1337/user/find?where={%22text%22:%20%22true%22}`
