### Install Jmeter
***
download from website:  
[https://jmeter.apache.org/download_jmeter.cgi](https://jmeter.apache.org/download_jmeter.cgi)  

### Setup Jmeter
***
change jmeter properties file `apache-jmeter-5.X\bin\jmeter.properties`  
    
set default language  

![set_jmeter_language](../../images/testing/jmeter/set_jmeter_language.png)

fix http return content encoding(or add beanshell)  
![properties_set_encoding.png](../../images/testing/jmeter/properties_set_encoding.png)
    
![beanshell_set_encoding.png](../../images/testing/jmeter/beanshell_set_encoding.png)  

### Jmeter Plugin
***
install plugin manager:  
[https://jmeter-plugins.org/wiki/PluginsManager/](https://jmeter-plugins.org/wiki/PluginsManager/)

### Jmeter Script
***
Jsr233 groovy script:
```groovy
//import other groovy file
GroovyShell shell = new GroovyShell()
script = shell.parse(new File("../script/commonFunctions.groovy"))
//call commonFunctions.groovy function "functionABC"
script.functionABC()

//parse prev json response data
import groovy.json.JsonSlurper;
def jsonSlurper = new JsonSlurper();
def response = jsonSlurper.parseText(prev.getResponseDataAsString());
vars.put("responData", response.responData.toString());
log.info("responData:" +  vars.get("responData"));
vars.put("key1", response.responData.key1.toString());
log.info("key1:" + vars.get("key1"));

//define global param
import groovy.transform.Field;
@Field param1;
@Field param2;
```

jmeter jexl3 script: 
```
//logic controller set time in 9:00 am and 9:00 pm
${__groovy("${__time(hh:mm a,)}"=="09:00 AM" || "${__time(hh:mm a,)}"=="09:00 PM")}
//logic controller set time every 5 minite
${__groovy("${__time(mm)%5 == 0}")}
```

