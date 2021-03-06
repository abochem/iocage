How to use templates
====================

**Templates can save you precious time!**

Set up a jail any way you like, and create a template from it. All packages and pre-configured settings will be available for deployment next time within seconds.  

Any jail can be converted to a template and back to a jail again as required. In fact a template is just another jail which has the property ``template`` set to "yes". The difference is that templates are not started by iocage, they are ignored!

**Here is how to do it with iocage:**

1. create a new jail ``iocage create tag=mytemplate``
2. configure the jail's networking
3. install any package you like and customize jail
4. once finished with customization stop the jail ``iocage stop UUID``
5. a good idea is set some notes ``iocage set notes="customized PHP,nginx jail" UUID``
6. turn the template property on ``iocage set template=yes UUID``
7. list your template with ``iocage list -t``

To create a new jail from this template simply clone it!

1. ``iocage clone UUID-of-mytemplate tag=mynewjail``
2. list new jail ``iocage list``
3. start jail ``iocage start UUID``

Done!

**If you need to make further customization in the template or want to patch it, you have two options.**

* convert template back to jail with ``iocage set template=no UUID-of-template``, and start the jail
* if you don't need network access to make the changes simply run ``iocage chroot UUID-of-template``, make the changes and exit

 
