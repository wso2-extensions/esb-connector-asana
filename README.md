# Asana EI Connector

The Asana [connector](https://docs.wso2.com/display/EI640/Working+with+Connectors) allows you to access the [Asana REST API](https://asana.com/guide/help/api/api) through WSO2 EI.
Asana is a web and mobile application designed to help teams track their work.



## Compatibility

| Connector version | Supported Asana API version | Supported WSO2 ESB/EI version |
| ------------- | ---------------|------------- |
| [1.0.0](https://github.com/wso2-extensions/esb-connector-asana/tree/org.wso2.carbon.connector.asana-1.0.0) | 1.0 |ESB 4.9.0, ESB 5.0.0, EI 6.1.1, EI 6.2.0, EI 6.3.0, EI 6.4.0    |

## Getting started

#### Download and install the connector

1. Download the connector from the [WSO2 Store](https://store.wso2.com/store/assets/esbconnector/details/9c710ae1-954a-487f-b098-afc0f90f6391) by clicking the Download Connector button.
2. Then you can follow this [Documentation](https://docs.wso2.com/display/EI640/Working+with+Connectors+via+the+Management+Console) to add and enable the connector via the Management Console in your EI instance.
3. For more information on using connectors and their operations in your EI configurations, see [Using a Connector](https://docs.wso2.com/display/EI640/Using+a+Connector).
4. If you want to work with connectors via EI tooling, see [Working with Connectors via Tooling](https://docs.wso2.com/display/EI640/Working+with+Connectors+via+Tooling).

#### Configuring the connector operations

To get started with Asana connector and their operations, see [Configuring Asana Operations](docs/config.md).

## Building From the Source

Follow the steps given below to build the Asana connector from the source code:

1. Get a clone or download the source from [Github](https://github.com/wso2-extensions/esb-connector-asana).
2. Run the following Maven command from the `esb-connector-asana` directory: `mvn clean install`.
3. The Asana connector zip file is created in the `esb-connector-asana/target` directory

## How You Can Contribute

As an open source project, WSO2 extensions welcome contributions from the community.
Check the [issue tracker](https://github.com/wso2-extensions/esb-connector-asana/issues) for open issues that interest you. We look forward to receiving your contributions.
