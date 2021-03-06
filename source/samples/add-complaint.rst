
.. code-block:: bash

    curl -s --user 'api:YOUR_API_KEY' \
	https://api.mailgun.net/v3/YOUR_DOMAIN_NAME/complaints \
	-F address='bob@example.com'

.. code-block:: java

 public static ClientResponse AddComplaint() {
 	Client client = new Client();
 	client.addFilter(new HTTPBasicAuthFilter("api",
 			"YOUR_API_KEY"));
 	WebResource webResource =
 		client.resource("https://api.mailgun.net/v3/YOUR_DOMAIN_NAME/" +
 				"complaints");
 	MultivaluedMapImpl formData = new MultivaluedMapImpl();
 	formData.add("address", "bob@example.com");
 	return webResource.type(MediaType.APPLICATION_FORM_URLENCODED).
 		post(ClientResponse.class, formData);
 }

.. code-block:: php

  # Include the Autoloader (see "Libraries" for install instructions)
  require 'vendor/autoload.php';
  use Mailgun\Mailgun;

  # Instantiate the client.
  $mgClient = new Mailgun('YOUR_API_KEY');
  $domain = 'YOUR_DOMAIN_NAME';
  
  # Issue the call to the client.
  $result = $mgClient->post("$domain/complaints", array('address' => 'bob@example.com'));

.. code-block:: py

 def add_complaint():
     return requests.post(
         "https://api.mailgun.net/v3/YOUR_DOMAIN_NAME/complaints",
         auth=("api", "YOUR_API_KEY"),
         data={'address': 'bob@example.com'})

.. code-block:: rb

 def add_complaint
   RestClient.post "https://api:YOUR_API_KEY"\
   "@api.mailgun.net/v3/YOUR_DOMAIN_NAME/complaints",
   :address => 'bob@example.com'
 end

.. code-block:: csharp

 public static IRestResponse AddComplaint() {
 	RestClient client = new RestClient();
 	client.BaseUrl = new Uri("https://api.mailgun.net/v3");
 	client.Authenticator =
 		new HttpBasicAuthenticator("api",
 		                           "YOUR_API_KEY");
 	RestRequest request = new RestRequest();
 	request.Resource = "{domain}/complaints";
 	request.AddParameter("domain",
 	                     "YOUR_DOMAIN_NAME", ParameterType.UrlSegment);
 	request.AddParameter("address", "bob@example.com");
 	request.Method = Method.POST;
 	return client.Execute(request);
 }

.. code-block:: go

 func CreateComplaint(domain, apiKey, emailAddress string) error {
   mg := mailgun.NewMailgun(domain, apiKey, "")
   return mg.CreateComplaint("bob@example.com")
 }
