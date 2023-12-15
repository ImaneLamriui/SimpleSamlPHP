# SimpleSamlPHP for secure access to web applications.
## Apache2 Server + PHP 8.1.2 +  Ubuntu Server 22.04 LTS
### Download packages:  sudo apt install php-xml php-mbstring php-curl php-memcache php-ldap memcached
### SimpleSAMLphp is an open-source implementation used to provide and to facilitate authentication and authorization services in web environments. Its primary purpose is to simplify and standardize the implementation of Single Sign-On (SSO) in web applications and services, especially in cases where secure and unified access to multiple applications and services is required.
### There is a new stable release, version, v2.1.1, of SimpleSAMLphp with a different directory structure. The configuration files now come with an additional '.dist' extension, The '.dist' extension indicates that these are distribution files or templates intended for customization. Users should copy these files without the '.dist' extension and modify them according to their specific configuration.
### The 'www' directory has been replaced with 'public'."
### There are some important configurations to consider to enable authentication, including activating the SQLAuth module. You can add this module to the authsources.php configuration file by setting 'sqlauth' to true. Ensure that you add the module if it is not already present in the configuration.
<p>Download <a href="https://github.com/simplesamlphp/simplesamlphp/releases/download/v2.1.1/simplesamlphp-2.1.1-full.tar.gz"> SimpleSamlPHP version2.1.1</a> </p>

