# Automated_Mailing
This repository contains a Python-based automated mailing system capable of sending personalized emails with attachments to multiple recipients.

Navigation Menu
ninjemail

Code
Issues
2
Pull requests
ninjemail
/README.md
david96182
david96182
7 months ago
360 lines (233 loc) · 16.5 KB

Preview

Code

Blame
Ninjemail logo

Python Badge PEP8 Badge HitCount Badge GitHub License Badge PRs Welcome Badge Test status Test coverage Badge

Ninjemail is a Python library designed to streamline the process of creating email accounts across various top email provider services. With Ninjemail, you can automate the creation of email accounts, saving time and effort. It provides an easy-to-use interface for creating accounts with customizable options.

Features
Automated Account Creation: Ninjemail streamlines the process of creating email accounts by automating the necessary steps.
Support for Major Email Providers: Ninjemail supports a wide range of popular email service providers including Gmail, Outlook and Yahoo, giving you flexibility in choosing the provider that suits your needs.
Python Integration: Ninjemail seamlessly integrates into Python projects, allowing for efficient automation of email account creation.
Auto-generated Account Details: Generate random account details for username, password, first name, last name, country, and birthdate if not provided, allowing for quick creation of multiple accounts for testing or other purposes.
Customizable Options: Customize account details such as username, password, first name, last name, country, and birthdate to meet your specific requirements.
Error Handling and Logging: Ninjemail provides error handling capabilities and logs activities to facilitate debugging and tracking of account creation actions.
Open-Source and Extensible: Being an open-source project, Ninjemail encourages contributions and allows for further extension and improvement of its functionalities.
Proxy Support: Ninjemail includes proxy support, giving users the option to use their own proxies for account creation, including support for authenticated proxies. This feature allows for enhanced privacy, security, and flexibility during the email account creation process.
Free Proxy Option: Additionally, Ninjemail offers an option to automatically retrieve and use free proxies. This feature provides users with a convenient solution for proxy usage, eliminating the need for purchasing or configuring proxies separately.
Installation
To install Ninjemail, you can follow these steps:

Clone the Ninjemail repository from GitHub using the following command:

Copy

git clone https://github.com/david96182/ninjemail.git
Change your current directory to the cloned repository:

Copy

cd ninjemail
Install the required dependencies using pip:

pip install -r requirements.txt
You can then proceed to use Ninjemail as described in the next instructions.

Testing
To ensure the reliability and correctness of this project, tests have been implemented using pytest. The test suite covers various aspects of the codebase and helps maintain the desired functionality as the project evolves.

Running Tests
Make sure you have the project's dependencies installed.

Navigate to the project's root directory.

Run the following command to execute the test suite:

pytest
Test Coverage
Comprehensive test coverage is prioritized to minimize bugs and regressions. The current code coverage can be measured using pytest-cov. To generate a coverage report, users can execute the following command:

pytest --cov
The coverage report will be displayed in the terminal.

Writing Tests
When adding new features or fixing bugs, it's important to include corresponding test cases to validate the changes. Tests should be placed in the tests/ directory, following a naming convention such as test_module.py or test_class.py. You can organize the tests based on the project's structure.

Usage
Importing the Library
To use Ninjemail in your Python script, import the Ninjemail class from the ninjemail module:

from ninjemail import Ninjemail
Initializing Ninjemail
To create an instance of Ninjemail, call the Ninjemail class with optional parameters:

ninja = Ninjemail(
    	browser="firefox", 
    	captcha_keys={"capsolver": "YOUR_API_KEY", "nopecha": "YOUR_API_KEY"}, 
    	sms_keys={"service_name": {"user": "USERNAME", "token": "TOKEN"}},
    	proxies=['http://ip:port', 'http://ip2:port2'],
    	auto_proxy=True
)
The browser parameter specifies the browser to be used for automation. The default value is "firefox". Currently, Ninjemail supports Firefox, Chrome and Undetected Chrome. The acceptable values for the browser parameter are firefox, chrome and undetected-chrome respectively.

The captcha_keys parameter is a dictionary that contains the API keys for supported captcha solving services, based on config.toml. The default value is an empty dictionary. You can provide API keys for specific captcha solving services if required. Currently, the following services are supported:

"capsolver"
"nopecha"
To provide the API keys for these services, you can pass a dictionary to the captcha_keys parameter. Each key-value pair in the dictionary corresponds to a captcha solving service and its respective API key as shown in the example above.

The sms_keys parameter is a dictionary that contains the API key/s for the SMS service/s, based on config.toml. The default value is an empty dictionary. You can provide an API key or keys for the SMS services if required. Currently, "getsmscode", "smspool" and "5sim" are supported.

The proxies parameter specifies the list of proxy servers to be used for the creation of email accounts. Is optional and can accept either a single proxy server or multiple proxy servers in a list. Each proxy should be provided as a string in the format "http://ip:port," where "ip" represents the IP address of the proxy server and "port" represents the port number. Additionally, support for authentication proxies is available, but exclusively for chrome and undetected-chrome for the moment. The format for authentication proxies remains the same: "http://username:password@ip:port".

The auto_proxy parameter is a boolean flag that determines whether Ninjemail should automatically obtain and rotate free proxies during automation tasks. If auto_proxy is set to True, Ninjemail will handle the process of acquiring and managing free proxies internally.

Please note that when auto_proxy is enabled, Ninjemail will handle the management of proxies, but the availability and reliability of free proxies may vary. It's important to consider the limitations and potential risks associated with using free proxy services.

Creating Outlook Accounts
To create an Outlook/Hotmail account using Ninjemail, call the create_outlook_account method:

ninja.create_outlook_account(
    		username="", 
    		password="", 
    		first_name="", 
    		last_name="", 
    		country="", 
    		birthdate="", 
    		hotmail=False,
    		use_proxy=True
)
The username parameter is the desired username for the Outlook account. If not provided, a random username will be generated.

The password parameter is the desired password for the Outlook account. If not provided, a random password will be generated.

The first_name parameter is the first name of the account holder. If not provided, a random first name will be generated.

The last_name parameter is the last name of the account holder. If not provided, a random last name will be generated.

The country parameter is the country of residence for the account holder. If not provided, a random country will be selected.

The birthdate parameter is the birthdate of the account holder in the format "MM-DD-YYYY". If not provided, a random birthdate will be generated.

The hotmail parameter is a boolean flag indicating whether to create a Hotmail account. The default value is False (i.e., creates an Outlook account).

The use_proxy parameter determines whether to use a proxy for the process of creating an Outlook account. If use_proxy is set to True, a proxy will be utilized during the account creation process. Default is True.
