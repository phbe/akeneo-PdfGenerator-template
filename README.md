# akeneo-PdfGenerator-template

This is a template for the Akeneo PdfGeneratorBundle.

## Install the template

To install this template you need to override the default template:

#####1. Create a new folder structure in the app/Resources directory
```
app/Resources/PimPdfGeneratorBundle/views/Product
```

#####2. Then add your new template to this folder, preserving the filename from the original bundle
```
renderPdf.html.twig 
```

#####3. Clear the cache
After overriding a template, you must clear the cache for the override to take effect, even in a development environment.

## Install the template in an existing akeneo demo vagrant box
#####1. Copy the template to your vagrant box folder

* Download the akeneo-PdfGenerator-template.zip from GitHub
* Unzip the file and copy the folder "akeneo-PdfGenerator-template" into your vagrant box folder


#####2. Edit the vagrant file
* Open the vagrant box folder and open the Vagrantfile in a texteditor
* Add the following lines to the file and save it

```
 config.vm.provision :file do |file|
    file.source = "akeneo-PdfGenerator-template/PimPdfGeneratorBundle/views/Product/renderPdf.html.twig"
    file.destination = "/home/vagrant/pim/app/Resources/PimPdfGeneratorBundle/views/Product/renderPdf.html.twig"
  end
```
######3. Shutdown the vagrant box and start it with provisioning
`$ vagrant up --provision`

######4. Clear the chache
```
$ vagrant ssh
$ php app/console cache:clear --env=prod
```

## Additional information

https://symfony.com/doc/current/templating/overriding.html

The template is a twig file and the file itself is a parameter for the PDF renderer service.
The original template is: src/Pim/Bundle/PdfGeneratorBundle/Resources/views/Product/renderPdf.html.twig

The pattern for overriding templates in this way is to create a folder with the name of the bundle class in the app/Resources directory. 
Then add your new template to this folder, preserving the directory structure from the original bundle.