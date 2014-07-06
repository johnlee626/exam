<?php

  require_once("../include/db_login.php");  

  $var_title = str_replace("+"," ",$_GET['title']);

  function displayQuestion($id)
  {
    $listing="";
    if(empty($id)){
      $query="SELECT * FROM `".$_GET['title']."` order by QID asc limit 1";
    }
    else{
      $query="SELECT * FROM `".$_GET['title']."` WHERE QID='".$id."'";
    }
  
    $result=mysql_query($query);
    if(!$result){
      die("Could not query the database: <br />");
    }
    $total_result=mysql_query("SELECT * FROM `".$_GET['title']."`");
    if(!$total_result){
      die("Could not query the database: <br />");
    }
    $total_rows = mysql_num_rows($total_result);  

    $listing.='<table width=100% border=0>
    <tr><td align=right>
    <br>';
    if(isset($_GET['id'])){
      if($_GET['id']>1)
        $listing.='<input id="submit-button" type=submit name="Submit" value="Previous" />&nbsp;&nbsp';
    }
    $listing.='<input id="submit-button" type=submit name="Submit" value="Check Answer" />&nbsp;&nbsp;';
    if(isset($_GET['id'])){
      if($_GET['id']!="" && $_GET['id']<$total_rows)
        $listing.='<input id="submit-button" type=submit name="Submit" value="Next" />';
      else if($_GET['id']=="" && $total_rows>1) $listing.='<input id="submit-button" type=submit name="Submit" value="Next" />';
    }
    else if($total_rows>1) $listing.='<input id="submit-button" type=submit name="Submit" value="Next" />';
    $listing.='</td></tr>
    </table>
    <br>

    <table width=100% border=0>';

    while($table = mysql_fetch_array($result)){      
      $listing.='<tr><td>Question '.$table[0].'/'.$total_rows.'</td></tr><tr><td>'.$table[1].'</td><tr>';
      if($table[2]!=""){
        $listing.='<tr><td><input type="radio" name="ans" value="1" ';
        if(isset($_GET['ans'])){
          if($_GET['ans']=='1') $listing.='checked';
        }
        $listing.='>&nbsp;'.$table[2];
        if(isset($_GET['ans'])){
          if($table[8]=='1')
            $listing.='&nbsp;<font color=green>Correct Answer</font>';
          if($_GET['ans']=='1' and $_GET['ans']!=$table[8])
            $listing.='&nbsp;<font color=red>Incorrect Answer</font>';
        }
        $listing.='</td><tr>';
      }
      if($table[3]!=""){ 
        $listing.='<tr><td><input type="radio" name="ans" value="2" ';
        if(isset($_GET['ans'])){
          if($_GET['ans']=='2') $listing.='checked';
        }
        $listing.='>&nbsp;'.$table[3];
        if(isset($_GET['ans'])){
          if($table[8]=='2')
            $listing.='&nbsp;<font color=green>Correct Answer</font>';
          if($_GET['ans']=='2' and $_GET['ans']!=$table[8])
            $listing.='&nbsp;<font color=red>Incorrect Answer</font>';
        }
        $listing.='</td><tr>';
      }
      if($table[4]!=""){ 
        $listing.='<tr><td><input type="radio" name="ans" value="3" ';
        if(isset($_GET['ans'])){
          if($_GET['ans']=='3') $listing.='checked';
        }
        $listing.='>&nbsp;'.$table[4];
        if(isset($_GET['ans'])){
          if($table[8]=='3')
            $listing.='&nbsp;<font color=green>Correct Answer</font>';
          if($_GET['ans']=='3' and $_GET['ans']!=$table[8])
            $listing.='&nbsp;<font color=red>Incorrect Answer</font>';
        }
        $listing.='</td><tr>';
      }
      if($table[5]!=""){ 
        $listing.='<tr><td><input type="radio" name="ans" value="4" ';
        if(isset($_GET['ans'])){
          if($_GET['ans']=='4') $listing.='checked';
        }
        $listing.='>&nbsp;'.$table[5];
        if(isset($_GET['ans'])){
          if($table[8]=='4')
            $listing.='&nbsp;<font color=green>Correct Answer</font>';
          if($_GET['ans']=='4' and $_GET['ans']!=$table[8])
            $listing.='&nbsp;<font color=red>Incorrect Answer</font>';
        }
        $listing.='</td><tr>';
      }
      if($table[6]!=""){ 
        $listing.='<tr><td><input type="radio" name="ans" value="5" ';
        if(isset($_GET['ans'])){
          if($_GET['ans']=='5') $listing.='checked';
        }
        $listing.='>&nbsp;'.$table[6];
        if(isset($_GET['ans'])){
          if($table[8]=='5')
            $listing.='&nbsp;<font color=green>Correct Answer</font>';
          if($_GET['ans']=='5' and $_GET['ans']!=$table[8])
            $listing.='&nbsp;<font color=red>Incorrect Answer</font>';
        }
        $listing.='</td><tr>';
      }
      if($table[7]!=""){ 
        $listing.='<tr><td><input type="radio" name="ans" value="6" ';
        if(isset($_GET['ans'])){
          if($_GET['ans']=='6') $listing.='checked';
        }
        $listing.='>'.$table[7];
        if(isset($_GET['ans'])){
          if($table[8]=='6')
            $listing.='&nbsp;<font color=green>Correct Answer</font>';
          if($_GET['ans']=='6' and $_GET['ans']!=$table[8])
            $listing.='&nbsp;<font color=red>Incorrect Answer</font>';
        }
        $listing.='</td><tr>';
      }    
      
      if($_GET['Submit']=="Check Answer"){      
        if(isset($_GET['ans'])){
          if(!empty($_GET['ans']))
            $listing.='<tr><td><b>Explanation: </b>'.$table[9].'</td></tr>';
        }
      }
    }       
    
    return $listing;
  }
  
  $connection=mysql_connect($db_host,$db_username,$db_password);
  if(!$connection){
    die("Could not connect to the database: <br />".mysql_error());
  }

  $db_select=mysql_select_db($db_database);
  if(!$db_select){
    die("Could not select the database: <br />".mysql_error());
  }

  if(isset($_GET['id'])){
    $listing=displayQuestion($_GET['id']);    
  }
  else $listing=displayQuestion('');

  if(isset($_GET['Submit'])){
    if($_GET['Submit']=="Previous"){
      if(isset($_GET['id'])){
        if(empty($_GET['id'])){
          header("Location: ../exam/?id=1");
          exit;
        }
        else{
          header("Location: ../exam/?title=".$_GET['title']."&id=".($_GET['id']-1));
          exit;
        }
      }      
    }
    else if($_GET['Submit']=="Check Answer"){      
      if(isset($_GET['ans'])){
        if(empty($_GET['ans'])) $error_message='<font color="red">Please choose an answer.</font>';
        else{
	    $connection=mysql_connect($db_host,$db_username,$db_password);
          if(!$connection){
          die("Could not connect to the database: <br />".mysql_error());
  }

          $db_select=mysql_select_db($db_database);
          if(!$db_select){
            die("Could not select the database: <br />".mysql_error());
          }

          if(isset($_GET['id'])){
            if(empty($_GET['id'])) $query="SELECT * FROM `".$_GET['title']."` order by QID asc limit 1";
            else $query="SELECT * FROM `".$_GET['title']."` WHERE QID='".$_GET['id']."'";
          }
          else $query="SELECT * FROM `".$_GET['title']."` order by QID asc limit 1";
          $result=mysql_query($query);
          if(!$result){
            die("Could not query the database: <br />");
          }
          else
          {
            /*$row = mysql_fetch_row($result);
            if($row[8]!=$_GET['ans']){
              $error_message='<font color="red">The answer selected is incorrect.</font>';
            }
            else $confirm_message='<font color="green">The answer selected is correct.</font>';*/
          }        
	    
        }
      }  
      else $error_message='<font color="red">Please choose an answer.</font>';
    }
    else if($_GET['Submit']=="Next"){
      if(isset($_GET['id'])){
        if(empty($_GET['id'])){
          header("Location: ../exam/?title=".$_GET['title']."&id=2");
          exit;
        }
        else{
          header("Location: ../exam/?title=".$_GET['title']."&id=".($_GET['id']+1));
          exit;
        }
      }       
    }    
  }
  else if(isset($_GET['editExam'])){ 
    if($_GET['editExam']!=""){
      
    }
  }
  else if(isset($_GET['deleteExam'])){ 
    if($_GET['deleteExam']!=""){
      $con=mysqli_connect($db_host,$db_username,$db_password,"exam");
	// Check connection
	if (mysqli_connect_errno())
  	{
	  echo "Failed to connect to MySQL: " . mysqli_connect_error();
  	}

      // Create table
	$sql="DROP TABLE ".$_GET['deleteExam'];

	// Execute query
	if (mysqli_query($con,$sql))
	{
	  $confirm_message='<font color="green">Exam '.$_GET['deleteExam'].' deleted.</font>';
  	}
	else
  	{
	  echo "Error deleting table: " . mysqli_error($con);
	}
    }
  }
  
?>

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">

<head>

<title>Exam Page</title>
<link rel="icon" type="image/ico" href="http://www.angelexam.com/favicon.png" />
<meta http-equiv="content-type" content="application/xhtml+xml; charset=UTF-8" />
<meta name="robots" content="index, follow, noarchive" />
<meta name="googlebot" content="noarchive" />

<link rel="stylesheet" type="text/css" media="screen" href="css/screen.css" />
<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.4/jquery.min.js"></script>
<script language="javascript">
$(document).ready(function()
{	

        $("#errorMsg").hide();
  
        $("#login_form").submit(function()
	{
                $("#errorMsg").show();
		//remove all the class add the messagebox classes and start fading
		$("#msgbox").removeClass().addClass('messagebox').text('Validating....').fadeIn(1000);
		//check the username exists or not from ajax
		$.post("ajax_login.php",{ user_name:$('#username').val(),password:$('#password').val(),rand:Math.random() } ,function(data)
        {
		  if(data=='yes') //if correct login detail
		  {
		  	$("#msgbox").fadeTo(200,0.1,function()  //start fading the messagebox
			{ 
			  //add message and change the class of the box and start fading
			  $(this).html('Logging in.....').addClass('messageboxok').fadeTo(900,1,
              function()
			  { 
			  	 //redirect to secure page
				 document.location='/';
			  });
			  
			});
		  }
		  else 
		  {
		  	$("#msgbox").fadeTo(200,0.1,function() //start fading the messagebox
			{ 
			  //add message and change the class of the box and start fading
			  $(this).html('Invalid login/password').addClass('messageboxerror').fadeTo(900,1);
			});		
          }
				
        });
 		return false; //not to post the  form physically
	});
	//now call the ajax also focus move from 
	/*$("#password").blur(function()
	{
		$("#login_form").trigger('submit');
	});*/
});
</script>

</head>

<body>

<!-- wrap starts here -->
<div id="wrap">		
	
	<!-- content -->
	<div id="content-outer" class="clear"><div id="content-wrap">
	
		<div id="content">			

					<?php 				            
						echo '<table width=100% cellpadding=2 cellspacing=0 border=0><tr><td style="font-size:20px;">
<b>Exam '.$_GET['title'].'</b>
</td></tr>
<tr>
    <td colspan="2" style="height:2px;"><hr size="1"></td>
</tr>
<tr><td>
<font class=small>Please choose an answer for each question then check the result.</font>
</td></tr></table>
';

echo '<table><tr><td>';
if(isset($error_message) && $error_message!='') {
  echo $error_message;					  
}
else if(isset($confirm_message) && $confirm_message!='') {
  echo $confirm_message;					  
}					
echo '&nbsp;</td></tr></table>';

echo '<form name="savechanges" method="get" action="'.$_SERVER['PHP_SELF'].'">
<input type="hidden" name=title value="'.$_GET['title'].'">
<input type="hidden" name=id value="';
if(isset($_GET['id'])) echo $_GET['id'];
echo '">';

echo $listing;
  
echo '</table></form>';				          
				        ?>					
					
		
		</div>	
			
	<!-- content end -->	
	</div></div>		
	
	
<!-- wrap ends here -->
</div>

</body>
</html>
