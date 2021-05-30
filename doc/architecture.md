# Cattlechain Architecture

CattleChain core platform is consist of various FIWARE Generic Enablers. Figure present the architecture of the CattleChain platform.

![Architecture](https://raw.githubusercontent.com/CattleChain/Docs/master/images/architecture.png)


## Generic Enablers

### KeyRock

Keyrock is the FIWARE component responsible for Identity Management. Using Keyrock (in conjunction with other security components such as PEP Proxy and Authzforce) enables you to add OAuth2-based authentication and authorization security to your services and applications.
The main identity management concepts within Keyrock are:
* Users:

 	* Have a registered account in Keyrock.
	* Can manage organizations and register applications.

* Organizations:

	* Are group of users that share resources of an application (roles and permissions).
	*	Users can be members or owners (manage the organization).

* Applications:

	* has the client role in the OAuth 2.0 architecture and will request protected user data.
	* Are able to authenticate users using their Oauth credentials (ID and secret) which unequivocally identify the application
	* Define roles and permissions to manage authorization of users and organizations
	* Can register Pep Proxy to protect backends.
	* Can register IoT Agents.

Keyrock provides both a GUI and an API interface.

to know more about keyrock please follow keyrock [documentation](https://fiware-idm.readthedocs.io/en/latest/).
