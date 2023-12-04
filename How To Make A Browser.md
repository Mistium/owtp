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
def "redirect" "url"
input_1 = url.destr
load = true
endef
load = false
mainloop:

loc 2 2 150 -50
input 280 20 "1" : c#333
owtp_url = "https://raw.githubusercontent.com/Mistium/owtp/main/"
get_url = input_1.replace("owtp://",owtp_url)
if get_url.right(4) == ".web" "get_url = get_url ++ "/index.osl""
onload = false
if "enter".pressed "load = true"
if load (
network "get" get_url
onload = true
if data != "loading" "load = false"
page_data = data
)
frame window_width / -2 window_height / 2 - 80 window_width / 2 window_height / -2 page_len
type = get_url.right(4)
loc 2 2 20 -20
run page_data.split(newline)
frame "clear"
import "win-buttons"
```
