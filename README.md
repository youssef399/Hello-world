# Hello-world
<?php
/*	FACEBOOK LOGIN BASIC - PHP SDK V4.0
 *	file 			- index.php
 * 	Developer 		- Krishna Teja G S
 *	Website			- http://packetcode.com/apps/fblogin-basic/
 *	Date 			- 27th Sept 2014
 *	license			- GNU General Public License version 2 or later
*/

/* INCLUSION OF LIBRARY FILEs*/
	require_once( 'lib/Facebook/FacebookSession.php');
	require_once( 'lib/Facebook/FacebookRequest.php' );
	require_once( 'lib/Facebook/FacebookResponse.php' );
	require_once( 'lib/Facebook/FacebookSDKException.php' );
	require_once( 'lib/Facebook/FacebookRequestException.php' );
	require_once( 'lib/Facebook/FacebookRedirectLoginHelper.php');
	require_once( 'lib/Facebook/FacebookAuthorizationException.php' );
	require_once( 'lib/Facebook/GraphObject.php' );
	require_once( 'lib/Facebook/GraphUser.php' );
	require_once( 'lib/Facebook/GraphSessionInfo.php' );
	require_once( 'lib/Facebook/Entities/AccessToken.php');
	require_once( 'lib/Facebook/HttpClients/FacebookCurl.php' );
	require_once( 'lib/Facebook/HttpClients/FacebookHttpable.php');
	require_once( 'lib/Facebook/HttpClients/FacebookCurlHttpClient.php');

/* USE NAMESPACES */
	
	use Facebook\FacebookSession;
	use Facebook\FacebookRedirectLoginHelper;
	use Facebook\FacebookRequest;
	use Facebook\FacebookResponse;
	use Facebook\FacebookSDKException;
	use Facebook\FacebookRequestException;
	use Facebook\FacebookAuthorizationException;
	use Facebook\GraphObject;
	use Facebook\GraphUser;
	use Facebook\GraphSessionInfo;
	use Facebook\FacebookHttpable;
	use Facebook\FacebookCurlHttpClient;
	use Facebook\FacebookCurl;

/*PROCESS*/

		// Demarrer la session
		session_start();
		
		// tester si le username si ce log 
		if(isset($_REQUEST('logout')))
		{
			unset($_SESSION['fb_token']
		}
	
	//1.Stat Session
	 session_start();
	//2.Use app id,secret and redirect url
	 $app_id = '';
	 $app_secret = '';
	 $redirect_url='http://localhost:8888/TestAlumni.html/index.php/';
	 
	 //3.Initialize application, create helper object and get fb sess
	 FacebookSession::setDefaultApplication($app_id,$app_secret);
	 $helper = new FacebookRedirectLoginHelper($redirect_url);
	 $sess = $helper->getSessionFromRedirect();
	 // Tester si la session de fac exists
	 if(isset($_SESSION['fb_token']){
	 	$ess = new FacebookSession($_SESSION['fb°token']);
	 }
	 // logout
	 
	 $logout = 'http://localhost:8888/TestAlumni.html/index.php= true '

	//4. if fb sess exists echo name 
	 	if(isset($sess)){
	 		//Store token in the php session
	 		$_SESSION['fb_token'] = $ess->getToken();
	 		//create request object,execute and capture response
		$request = new FacebookRequest($sess, 'GET', '/me');
		// from response get graph object
		$response = $request->execute();
		$graph = $response->getGraphObject(GraphUser::className());
		// use graph object methods to get user details
		$name= $graph->getName();
		$id= $graph->getid();
		$image = 'https://graph/facebook.com/'.$id.'/picture'?width=300';
		$email = "your email is $email <br><br>";
		echo  "<img src='$image' /> <br><br>";
		echo "hi $name";
		echo '<a href = ' " .$logout." '><button>logout</button></a>"
	}else{
		//else echo login
		echo '<a href='.$helper->getLoginUrl().'>Login with facebook</a>';
	}

