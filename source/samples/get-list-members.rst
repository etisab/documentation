
.. code-block:: bash

    curl -s --user 'api:YOUR_API_KEY' -G \
	https://api.mailgun.net/v3/lists/LIST@YOUR_DOMAIN_NAME/members/pages

.. code-block:: java

 public static ClientResponse ListingMembers() {
 	Client client = Client.create();
 	client.addFilter(new HTTPBasicAuthFilter("api",
 			"YOUR_API_KEY"));
 	WebResource webResource =
 		client.resource("https://api.mailgun.net/v3/lists/" +
 				"LIST@YOUR_DOMAIN_NAME/members/pages");
 	return webResource.get(ClientResponse.class);
 }

.. code-block:: php

  # Include the Autoloader (see "Libraries" for install instructions)
  require 'vendor/autoload.php';
  use Mailgun\Mailgun;

  # Instantiate the client.
  $mgClient = new Mailgun('YOUR_API_KEY');
  $listAddress = 'LIST@YOUR_DOMAIN_NAME';

  # Issue the call to the client.
  $result = $mgClient->get("lists/$listAddress/members/pages", array(
      'subscribed' => 'yes',
      'limit'      =>  5
  ));

.. code-block:: py

 def list_members():
     return requests.get(
         "https://api.mailgun.net/v3/lists/LIST@YOUR_DOMAIN_NAME/members/pages",
         auth=('api', 'YOUR_API_KEY'))

.. code-block:: rb

 def list_members
   RestClient.get("https://api:YOUR_API_KEY" \
                  "@api.mailgun.net/v3/lists/LIST@YOUR_DOMAIN_NAME/members/pages")
 end

.. code-block:: csharp

 public static IRestResponse ListingMembers() {
 	RestClient client = new RestClient();
 	client.BaseUrl = new Uri("https://api.mailgun.net/v3");
 	client.Authenticator =
 		new HttpBasicAuthenticator("api",
 		                           "YOUR_API_KEY");
 	RestRequest request = new RestRequest();
 	request.Resource = "lists/{list}/members/pages";
 	request.AddParameter("list", "LIST@YOUR_DOMAIN_NAME", ParameterType.UrlSegment);
 	return client.Execute(request);
 }

.. code-block:: go

 func GetMembers(domain, apiKey string) (int, []mailgun.Member, error) {
   mg := mailgun.NewMailgun(domain, apiKey, "")
   return mg.GetMembers(-1, -1, mailgun.All, "LIST@YOUR_DOMAIN_NAME")
 }
