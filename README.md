htmlpage Dashboard()
<%{
    myCases = Add_Case[Case_Owner.Email == zoho.loginuserid].count();
    myOpenCases = Add_Case[(((Case_Owner.Email == zoho.loginuserid && Case_Status != "Resolved") && Case_Status != "Closed") && Case_Status == "Open")].count();
    allOpenCases = Add_Case[((Case_Status != "Resolved" && Case_Status != "Closed") && Case_Status == "Open")].count();
    escalatedCases = Add_Case[((Case_Status is not null) && Case_Status == "Escalated")].count();
    myTeamOpencases = Add_Case[(((Department.Manager_Email == zoho.loginuserid && Case_Status != "Resolved") && Case_Status != "Closed") && Case_Status == "Open")].count();
    myTeamMembers = Employees[Department.Manager_Email == zoho.loginuserid].count();
    casesOfCustomer = Add_Case[Caller.Email == zoho.loginuserid].count();
    mycaseComments = Case_Comments[(Callers.Email == zoho.loginuserid && Case_Owner.Email == zoho.loginuserid)].count();
    ClientName  =  Callers  [Email == zoho.loginuserid];
    AgentName  =  Employees  [Email == zoho.loginuserid];
    managerName  =  Managers  [Email == zoho.loginuserid];
    isAdmin = thisapp.user.isAdmin();
    isCustomer = thisapp.user.isCustomers();
    isEmployee = thisapp.user.isEmployees();
    isManager = thisapp.user.isManager();%>    <style>
  <%=thisapp.style.home()%>
  .quizsection {
float: left;
width:65%;
margin:5% 0 0% 20%;
border: 1px solid #e8e8e8;
padding: 20px;
border-radius: 10px;
background-color:#e8e8e8;
}
.box{
  border: 1px solid #d6d6d6;
box-shadow: 0 1px 3px rgba(100,100,100,0.1);
margin-bottom: 15px;
border-radius: 3px 3px 0 0;
overflow: visible;
position: relative;
}

.box-title{text-align: center;
padding: 10px 15px;
margin-buttom: 10px;
background-color: #f8f8f8;
background-image: -moz-linear-gradient(top, #fdfdfd, #f6f6f6);
background-image: -ms-linear-gradient(top, #fdfdfd, #f6f6f6);
background-image: -webkit-gradient(linear, 0 0, 0 100%, from(#fdfdfd), to(#f6f6f6));
background-image: -webkit-linear-gradient(top, #fdfdfd, #f6f6f6);
background-image: -o-linear-gradient(top, #fdfdfd, #f6f6f6);
background-image: linear-gradient(top, #fdfdfd, #f6f6f6);
border-bottom: 1px solid #d6d6d6;
color: #555555;
text-shadow: 0 1px 0 #ffffff;
font-size: 14px;
font-weight: bold;
}
.container-fluidstudent {
width: 80%;
padding-left: 10%;
padding-right: 20px;
padding-bottom: 30px;
}
.container-fluidtutor
{
	width:100%;
}

  </style><%if (isAdmin)
    {%>        <div class="container-fluid quizsection " id="container">
									 
                   <div class="row-fluid">
                   <div class="span12" id="content">
                    <div class="row-fluid quick-actions">
                    </div>
					<div class="row-fluid">
                        <div class="span4">
                            <div class="box">
                                <div class="box-title">My Cases</div>
                                <div class="box-content"><a style = "text-align:center"href="#View:My_Cases"><h1> <%=myCases%></h1></a></div>
                            </div>
                        </div>
						 
						
								<div class="span4"style="">
									<div class="box">
										<div class="box-title">My Open Cases</div>
										<div class="box-content"><a style = "text-align:center"href="#View:My_Open_Cases"><h1> <%=myOpenCases%></h1></a></div>
									</div>
								</div> 
						 		 <div class="span4">
									<div class="box">
										<div class="box-title">All Open Cases</div>
										<div class="box-content"><a style = "text-align:center"href="#View:All_Open_Cases"><h1> <%=allOpenCases%></h1></a></div>
									</div>
								</div> 
                              <div class="span4" >
									<div class="box" style="border-radius: 5px;">
										<div class="box-title">Escalated Cases</div>
										<div class="box-content"><a style = "text-align:center"href="#View:Escalated_Cases"><h1> <%=escalatedCases%></h1></a></div>
									</div>
								</div> 
                    </div>
					
					
                    <div class="row-fluid">
                  
                            <div class="box">
						
							  <iframe width='750' height="295" frameborder='0' allowTransparency='true'  src='https://creator.zohopublic.com/aorborc/customer-service/report-embed/Cases_Report/mdbPw99mBR3JqeuUh8qJdWymCAjkdfXvv4WRdku6sbtv7Xe31AaRCWAf8A736xhu5mD9N2v1WObOqrj6RMFs7m1Xgrp9bkknCTed/?zc_Header=true' style ="padding-left: 3px;padding-right: 3px;"></iframe>
                       
                            </div>    <%}
    else if (isCustomer  &&  !isAdmin)
    {%>        <div class="quizsection">  <div class="container-fluidstudent  nopadding ">
            <div class="row-fluid ">
					<div class="span12">
                   <div id="header" style="
    background-image: -webkit-gradient(linear, 0 0, 0 100%, from(rgba(245, 185, 56, 1)), to(rgba(245, 16, 173, 0.61)));
    border-radius: 4px;">
                     <div id="userinfo" class="column"><span><strong>Welcome, <%=ClientName.Name%></strong></span></div>
						<div class="hright">
							<div id="userinfo" class="column"><a class="userinfo dropown-toggle" data-toggle="dropdown" href=""><img alt="" src="http://www.aorborc.com/lab/course/images/comments-vatar.jpg" width="25" /></a></div>
							
						</div
							
							
                    </div>
                </div>
							
				
            </div>
            </div>
							
		        <div class="container-fluid7" id="container">
                    <div class="row-fluid">
                    <div class="span12" id="content">
					<div class="row-fluid">
						
						    <div class="span6" style ="margin-left:10%">
                            <div class="box">
							<style>.row-fluid .span6 {
											/* padding: 20; */
											width: 40%;
											} </style>
                                <div class="box-title" >My Cases</div>
                                <div class="box-content"><a style = "text-align:center"href="#View:All_Cases_of_this_Customer"><h1><%=casesOfCustomer%></h1></a></div>
                                
                            </div>
						    </div>
						    <div class="span6" style ="margin-left:10%">
                            <div class="box">
                                <div class="box-title">My Case Comments</div>
							    <div class="box-content"><a style = "text-align:center"href="#View:My_Case_Comments"><h1><%=mycaseComments%></h1></a></div>
                            </div>
                            </div>
                    </div> 
                    </div>
                    </div> 
                    </div>
							   <style>.container-fluid7 {
								
								width: 600px;
							
								padding-bottom: 30px;
								}</style>
					<div class="container-fluid7"  id="container">
                    <div class="row-fluid">
					<div class="span12" id="content" style="margin-left:10%">
					<div class="row-fluid">
                           
        
                  <div class="span6">
				  <div class="form-actions"><a href="#View:All_Cases_of_this_Customer"class="btn btn-primary" style="background-image: -webkit-gradient(linear, 0 0, 0 100%, from(rgba(190, 22, 47, 0.63)), to(rgba(242, 50, 5, 1)));margin-left:20%">My Current Cases</a></div> </div>    <%}
    else if (isEmployee)
    {%>        <div class="quizsection">  <div class="container-fluidstudent  nopadding ">
            <div class="row-fluid ">
					<div class="span12">
                   <div id="header" style="
    background-image: -webkit-gradient(linear, 0 0, 0 100%, from(rgba(245, 185, 56, 1)), to(rgba(245, 16, 173, 0.61)));
    border-radius: 4px;">
                     <div id="userinfo" class="column"><span><strong>Welcome, <%=AgentName.FirstName%><%=AgentName.LastName%></strong></span></div>
						<div class="hright">
							<div id="userinfo" class="column"><a class="userinfo dropown-toggle" data-toggle="dropdown" href="#View:My_Profile"><img alt="" src="http://www.aorborc.com/lab/course/images/comments-vatar.jpg" width="25" /></a></div>
							
						</div
							
							
                    </div>
                </div>
							
				</div>
            </div>
							
		        <div class="container-fluid7" id="container">
                    <div class="row-fluid">
                    <div class="span12" id="content">
					<div class="row-fluid">
						
						    <div class="span6" style ="margin-left:10%">
                            <div class="box">
							<style>.row-fluid .span6 {
											/* padding: 20; */
											width: 40%;
											} </style>
                                <div class="box-title" >My Open Cases</div>
                                <div class="box-content"><a style = "text-align:center"href="#View:My_Open_Cases1"><h1><%=myOpenCases%></h1></a></div>
                                
                            </div>
						    </div>
						    <div class="span6" style ="margin-left:10%">
                            <div class="box">
                                <div class="box-title">My Cases</div>
							    <div class="box-content"><a style = "text-align:center"href="#View:My_Cases1"><h1><%=myCases%></h1></a></div>
                            </div>
                            </div>
                    </div> 
                    </div>
                    </div> 
                    </div>
							   <style>.container-fluid7 {
								
								width: 600px;
							
								padding-bottom: 30px;
								}</style>
					<div class="container-fluid7"  id="container">
                    <div class="row-fluid">
					<div class="span12" id="content" style="margin-left:10%">
					<div class="row-fluid">
                  <div class="span6">
				  <div class="form-actions"><a href="#View:My_Case_Comments"class="btn btn-primary" style="background-image: -webkit-gradient(linear, 0 0, 0 100%, from(rgba(190, 22, 47, 0.63)), to(rgba(242, 50, 5, 1)));margin-left:20%">My Case Comments</a></div>
				  <div class="form-actions"><a href="#View:My_Profile"class="btn btn-primary" style="background-image: -webkit-gradient(linear, 0 0, 0 100%, from(rgba(190, 22, 47, 0.63)), to(rgba(242, 50, 5, 1)));margin-right:20%">My Profile</a></div></div>    <%}
    else if (isManager)
    {%>        <div class="quizsection"> <div class="container-fluidtutor nopadding">
                 <div class="row-fluid">
			    <div class="span12">
                  <div id="header" style="
    background-image: -webkit-gradient(linear, 0 0, 0 100%, from(rgba(245, 185, 56, 1)), to(rgba(245, 16, 173, 0.61)));
    border-radius: 4px;">
                     <div id="userinfo" class="column"><span><strong>Welcome,<%=managerName.FirstName%><%=managerName.LastName%></strong></span></div>
						<div class="hright">
							<div id="userinfo" class="column"><a class="userinfo dropown-toggle" data-toggle="dropdown" href="#View:My_Profile"><img alt="" src="http://www.aorborc.com/lab/course/images/comments-vatar.jpg" width="25" /></a></div>
						</div>
                    </div>
                </div>
				</div>
				</div> <style>
							.row-fluid .span6
							{
								width: 28%;
							} 
							</style>
			        <div class="container-fluidtutor" id="container">
                    <div class="row-fluid" >
                    <div class="span12" id="content">
					<div class="row-fluid" style="MARGIN: 0 50px;">
						<div class="span6">
						<div class="box">
						<div class="box-title">My Team Open Cases</div>
						<div class="box-content"><h3><a href="#View:My_Team_s_Open_Cases"><%=myTeamOpencases%></a></h3></div>
						</div>
						</div>
						
						<div class="span6">
						<div class="box">
						<div class="box-title">Escalated Cases</div>
						<div class="box-content"><h3><a href="#View:Escalated_Cases"><%=escalatedCases%></a></h3></div>
						</div>
						</div>
						
						<div class="span6">
						<div class="box">
						<div class="box-title">My Team Members</div>
						<div class="box-content"><h3><a href="#View:My_Team_Members"><%=myTeamMembers%></a></h3></div>
						</div>
						</div>
	
                    </div> 
                    </div>
                    </div> 
                    </div>
							   
							  
							   <div class="container-fluidtutor" id="container" style ="margin-left:10%;">
                    <div class="row-fluid">
                    <div class="span12" id="content">
					<div class="row-fluid">
						<div class="span6">
							 <div class="form-actions"><a href="#View:My_Profile" class="btn-primary" style="background-image: -webkit-gradient(linear, 0 0, 0 100%, from(rgba(190, 22, 47, 0.63)), to(rgba(242, 50, 5, 1)));">My Profile</a></div>
						</div>
						 <div class="span6">
							 <div class="form-actions"><a href="#View:My_Team_s_Open_Cases" class="btn-primary" style="background-image: -webkit-gradient(linear, 0 0, 0 100%, from(rgba(190, 22, 47, 0.63)), to(rgba(242, 50, 5, 1)));">My Team Open Cases</a></div>
                        </div>
                    </div> 
                    </div>
                    </div> 
                    </div>  </div>    <%}
}%>
