# Setup

Making a basic browser is relatively easy in osl

To start with you will need to ask for the network permission to ensure you can actually access the internet, to do this run the command below:
```
permission "request" "network"
```
You can check you have the permission by running
```
permission "get"
if permissions.contains("network") (

  // code you want to run

)
```
After you have this permission you can then run commands such as:

```
network "get" [url] (requests a url or a cached webpage if available)

and

network "clear" [url] (deletes the cached webpage)
```

Using this you can easily write (as long as you know basic osl) a pretty simple web requester

```
window "show"
mainloop:

loc 2 2 150 -20
input 280 20 "1" : c#333
get_url = "https://raw.githubusercontent.com/Mistium/owtp/" ++ input_1.replace("owtp://","")
if get_url.left(4) == ".web" "get_url = get_url ++ "/index.osl""
network "get" get_url

frame window_width / -2 window_height / 2 - 40 window_width / 2 window_height / -2 page_len
type = get_url.left(4)
if type == ".osl" (
run data
)
```
