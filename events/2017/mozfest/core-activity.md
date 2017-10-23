# Hacking the core


**Facilitators @Toshbrown @yousefamar @jptmoore @sevenEng** 

This session will give an overview of the core of Databox and how to fix issues and add new functionally. 
After a short presentation let the hacking commence. There will be a number of experienced  Databox devs on hand to get you started with your own idea. Not sure where to start why not have a go at one of theses: 
 
 1. Improving the install and deployment process using [LinuxKit](https://github.com/linuxkit/linuxkit) (Skills: docker and LinuxKit)  
    - Currently, the install process for Databox is very involved
    - This project will explore using LinuxKit to build a lightweight VM with containerd to encapsulate Databox.
    - This will enable the quick and easy deployment on MacOS, Linux and Windows 10 pro  
    - and as a bonus would eventually ([see](https://github.com/me-box/databox/issues/56)) allow small native installs on a raspberry PI 3 see PR [here](https://github.com/linuxkit/linuxkit/pull/2612)

 2. There is currently no lib-ocaml-databox (Skills: OCaml and/or ReasonML) .  
    - The [export-service](https://github.com/me-box/core-export-service) and [store-timeseries](https://github.com/me-box/store-timeseries)have most of the required code. 
    - A nice activity would be to pull these together into a library and some hello world apps. 
 
 3. Integrating the new ZMQ based store  (Skills: ReasonML / Golang / NodeJs / Binary Protocols)   
    - ReasonML based client and server [jptmoore/zest](https://github.com/jptmoore/zest)  
    - A Dataabox store implemented [/me-box/store-timeseries-zmq](https://github.com/me-box/store-timeseries-zmq)   
    - There is a partial Golang client available [toshbrown/goZestClient](https://github.com/Toshbrown/goZestClient)  
    - Creating a nodejs client would also be a useful task.
    - Building apps and driver to test this new store or any help testing and/or benchmarking would be fantastic.
 

 4. Designing an Image API for the new store.
 
 The store supports json, text and binary data being stored as key/values. A time series store exists for json data. I useful high-level API addition would be capability to store images by utilising both the key/value and time series stores. For example, a single image write could store the binary image within a key/value store but generate json meta-data based on the image to go to the time series store. This meta-data could be generated by using Exif data present in the image. A UUID could be used as the link between the key/value and time series store such that the image is stored using the UUID as the key. A useful activity would be to design and build such an API call using the existing store functionality.
    

 5. Add a UI to the export service (Skills: OCaml + web) . 
     - All data leaving the Databox goes through the export service. But there is currently no way to inspect this data.
     - Adding an interface to let people inspect what is being exported from their databox would ve a valuable contribution 
  
 6. Add a UI to the data stores (Skills: OCaml + web)
    - List the available data sources in a nice UI 
    - this would be beneficial for development as well as end users
 
 7. Improving unit and integration tests (Intergration testing / phantomjs / ect)
     - [see](https://github.com/me-box/databox/blob/master/TESTING.md) 
     - Currently, tests only exercise the API not the UI
     - Any improvements would be greatly received 