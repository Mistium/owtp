# OWTP

Origin web transfer protocol is the name for the website system contained within originOS and the summit web browser

## Input structure

owtp://websitename.web?input=data&input2=data2

osl files can then use "passed_input" <- this is a variable that is equal to "data"
and "passed_input2" <- this is a variable equal to "data2"

these can be anything, for example "passed_referer"


^^ The website name should be entered and end in ".web"

## Folder Structure

website.web
- index.osl
- webpage.osl
- directory1
  - index.osl
  - file1
  - file2
- directory2
  - index.osl
  - file1
  - file2
 
### example urls to access pages of this website
  
owtp://website.web/directory1 (grabs index.osl)

owtp://website.web/directory1/file2

owtp://website.web/directory2/index.osl
