

## Getting Started on OSX

Get the pre-requisites for ASP.NET/DNX

```
    brew tap aspnet/dnx
    brew update
    brew install dnvm
    dnvm upgrade
```

Add the following to the ~/.bash_profile or ~/.bashrc file:

```
    source dnvm.sh
```

Install yo and gulp

```
    npm install -g yo gulp
    npm install -g generator-aspnet
```

Install the generator and run it

```
    yo aspnet --gulp
```

Choose Web API Application


Your project is now created, you can use the following commands to get going

```
    dnu restore
    dnu build
    dnx . kestrel
    #dnx . run for console projects
    #dnx . kestrel or dnx . web for web projects
```

browse to [http://localhost:5001/api/values](http://localhost:5001/api/values)

## Tips 

### Quitting Kestrel

Quit kestrel with `q`

### dnxmon

Run dnx server continuously with nodemon watching for changes to cs or json files

```bash
dnxmon() {
    # Run dnx server continuously with nodemon watching for changes to cs or json files
    # Usage:
    #   dnxmon <directory> <command>
    # dnxmon (applies the defaults: current directory and the "web" command)
    
    dnxmonFn() {
        nodemon --ext "cs,json" --exec "dnx $1 $2"
    }
    
    if [[ $# -eq 0 ]]
    then
        echo "running default ..."
        echo "nodemon --ext \"cs,json\" --exec \"dnx . kestrel\""
        dnxmonFn . kestrel
    else
        if [[ $# -eq 2 ]]
        then
            echo "nodemon --ext \"cs,json\" --exec \"dnx $1 $2\""
            dnxmonFn $1 $2
        else
            echo "must supply directory and command such as dnxmon . kestrel"
        fi
    fi
}
```


