# Home Assistant and VOLTTRON Integration
The VOLTTRON driver available in this folder can be used to integrate [VOLTTRON](https://github.com/VOLTTRON/volttron) and [Home Assistant](https://home-assistant.io/). Because of this integration, the information about the components loaded on Home-Assistant such as thermostats and water heaters are available on the VOLTTRON message bus and other agents can use this information or make changes to them.

The home assistant agent was implemented as a driver so different agents can communicate with the devices available on home assistant automation system without knowing that those devices are loaded on home assistant. Also, all the devices information can be captured and store by the [Historian agent]( http://volttron.readthedocs.io/en/4.0/core_services/historians/index.html). Before running the driver, both VOLTTRON and home-assistant should be installed and running. To install and run home-assistant, please follow the instruction on this link: https://home-assistant.io/getting-started/ .

Since home-assistant provides a RESTful API, that API is used for the integrations. To use the home assistant driver, the [homeassistant.py]( https://github.com/heliazandi/volttron-applications/blob/master/ornl/HomeAssistant-VOLTTRON-Integration-Agents/HomeAssistantDriver/homeassistant.py) file located in this folder should be copied in  [volttron/services/core/MasterDriverAgent/master_driver/interfaces/](https://github.com/VOLTTRON/volttron/tree/master/services/core/MasterDriverAgent/master_driver/interfaces) folder. The [homeassistant.config]( https://github.com/heliazandi/volttron-applications/blob/master/ornl/HomeAssistant-VOLTTRON-Integration-Agents/HomeAssistantDriver/homeassistant.config) located in this folder can be used for configuring the driver. The “device address” parameter in the configuration file should be changed to the Home Assistant API URL. The configuration file can be store in VOLTTRON configuration store folder by using the following command:

volttron-ctl config store platform.driver devices/homeassistant homeassistant.config


For more details on how to store the configuration file, follow the [driver configuration]( http://volttron.readthedocs.io/en/4.1/core_services/drivers/Driver-Configuration.html) instructions. After adding the device configuration for the home assistant driver, the [Master Driver Agent]( https://github.com/VOLTTRON/volttron/tree/master/services/core/MasterDriverAgent) can be packaged, configured, installed , and run like any other agents on VOLTTRON platform.  

Note that the logic used and explained here can be used for integrating any energy management system that provides an API regardless of the programming language used by that system.



