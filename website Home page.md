<html>

<head>

		
	<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>

<script type="text/javascript" src="stepcarousel.js">



</script>


<script>
d = new Date();
document.getElementById("data").innerHTML = d.toString();
</script>

<script type="text/javascript">



var imageclock=new Object()
	//Enter path to clock digit images here, in order of 0-9, then "am/pm", then colon image:
	imageclock.digits=["c0.gif", "c1.gif", "c2.gif", "c3.gif", "c4.gif", "c5.gif", "c6.gif", "c7.gif", "c8.gif", "c9.gif", "cam.gif", "cpm.gif", "colon.gif"]
	imageclock.instances=0
	var preloadimages=[]
	for (var i=0; i<imageclock.digits.length; i++){ //preload images
		preloadimages[i]=new Image()
		preloadimages[i].src=imageclock.digits[i]
	}

	imageclock.imageHTML=function(timestring){ //return timestring (ie: 1:56:38) into string of images instead
		var sections=timestring.split(":")
		if (sections[0]=="0") //If hour field is 0 (aka 12 AM)
			sections[0]="12"
		else if (sections[0]>=13)
			sections[0]=sections[0]-12+""
		for (var i=0; i<sections.length; i++){
			if (sections[i].length==1)
				sections[i]='<img src="'+imageclock.digits[0]+'" />'+'<img src="'+imageclock.digits[parseInt(sections[i])]+'" />'
			else
				sections[i]='<img src="'+imageclock.digits[parseInt(sections[i].charAt(0))]+'" />'+'<img src="'+imageclock.digits[parseInt(sections[i].charAt(1))]+'" />'
		}
		return sections[0]+'<img src="'+imageclock.digits[12]+'" />'+sections[1]+'<img src="'+imageclock.digits[12]+'" />'+sections[2]
	}

	imageclock.display=function(){
		var clockinstance=this
		this.spanid="clockspan"+(imageclock.instances++)
		document.write('<span id="'+this.spanid+'"></span>')
		this.update()
		setInterval(function(){clockinstance.update()}, 1000)
	}

	imageclock.display.prototype.update=function(){
		var dateobj=new Date()
		var currenttime=dateobj.getHours()+":"+dateobj.getMinutes()+":"+dateobj.getSeconds() //create time string
		var currenttimeHTML=imageclock.imageHTML(currenttime)+'<img src="'+((dateobj.getHours()>=12)? imageclock.digits[11] : imageclock.digits[10])+'" />'
		document.getElementById(this.spanid).innerHTML=currenttimeHTML

	}


</script>



<style>
	
	body {
		background: #f6f6f6;
			}
	
	#header {
		width: 100%;
		height: 80px;
		border-bottom: 1px solid black;
		background:#15eaca;
	}
	
	#logo {
		height: 80px;
		width: 120px;
		
		text-align: center;
	}
	
	.button {
		height: 50px;
		width: 720px;
		margin: auto;
		
		margin-top: -41px;
		
	}
	
	.but {
		width: 80px;
		height: 40px;
	
		float: left;
		border: 1px solid black;
		font-size: 14px;
		background: #0461e4;
		color: black;
	}
	
	
	.subbutton {
		height: 32px;
		width: 390px;
		margin: auto;
		
		text-align: center;
		border-bottom: 1px solid black;
	}
	
	#data {
		height: 40px;
		width: 140px;
		
		text-align: center;
		margin-left: 90%;
		margin-top: -70px;
	}
	
	
	.box {
		width: 480px;
		height: 500px;
		border: 1px solid black;
	}
	
	.casuta {
		width: 200px;
		height: 200px;
		border: 1px solid black;
		margin-left: 10%;
		margin-right: 10%;
		margin-top: 10%;
		
	}
	
	.casutamica {
		width: 200px;
		height: 400px;
		
		margin-left: 55%;
		margin-right: 20%;
		margin-top: -42%;
		
	}

	
	
	#muie {
		margin-left: 50%;
	}
	
	#linie {
		height: 2px;
		background: black;
		width: 600px;
		margin: auto;
		margin-top: -30px;
	}
	
	#mare {
		height: 600px;
		width: 650px;
		margin: auto;
		
		margin-top: 20px;
	}
	
	.ima {
		width: 150px;
		height: 150px;
		border: 1px solid #f6f6f6;
		float: left;
		margin-left: 10px;
		margin-top: 5px;
	}
	
	
	#ceas {
		margin-top: -30px;
	}
	
	
	
	.stepcarousel{
position: relative; /*leave this value alone*/

overflow: scroll; /*leave this value alone*/
width:100%; /*Width of Carousel Viewer itself*/
height: 520px; /*Height should enough to fit largest content's height*/
-webkit-box-sizing: border-box; /* set box model so container width and height value includes any padding/border defined */
-moz-box-sizing: border-box;
box-sizing: border-box;
margin-top: 3%;

}

.stepcarousel .belt{
position: absolute; /*leave this value alone*/
left: 0;
top: 0;
}

.stepcarousel .panel{
float: left; /*leave this value alone*/
overflow: hidden; /*clip content that go outside dimensions of holding panel DIV*/
margin: 10px; /*margin around each panel*/
width: 500px; /*Width of each panel holding each content. If removed, widths should be individually defined on each content DIV then. */
}

span.paginatecircle{ /* CSS for paginate circle spans. Required */
background: white;
border: 2px solid black;
border-radius: 10px;
width: 6px;
height: 6px;
cursor: pointer;
display: inline-block;
margin-right: 4px;

}

span.paginatecircle:hover{
background: gray;
}

span.paginatecircle.selected{
background: black;
}

#poza {
	margin-left: 57%;
	margin-top: -1.5%;
	
	position: absolute;
}


	
</style>


<script type="text/javascript">

stepcarousel.setup({
	galleryid: 'mygallery', //id of carousel DIV
	beltclass: 'belt', //class of inner "belt" DIV containing all the panel DIVs
	panelclass: 'panel', //class of panel DIVs each holding content
	autostep: {enable:true, moveby:1, pause:3000},
	panelbehavior: {speed:500, wraparound:true, wrapbehavior:'slide', persist:true},
	defaultbuttons: {enable: true, moveby: 1, leftnav: ['arrowl.gif', -5, 80], rightnav: ['arrowr.gif', -20, 80]},
	
	contenttype: ['inline'] //content setting ['inline'] or ['ajax', 'path_to_external_file']
})

</script>


</head>




<body>




<div id="header">
	
	<a hre=""><div id="logo"> <h1>  </h1> </div></a>
	
	<div class="button">
			<a href="index.html">	<div class="but">  HOME  </div> </a>
				<a href="page.html"><div class="but">  WORLD VIEWS    </div></a>
				<a href="page.html"><div class="but">  SPORTS   </div></a>
				<a href="page.html"><div class="but">  TECHNO LOGY   </div></a>
				<a href="page.html"><div class="but">  STOCK MARKET   </div></a>
				<a href="search.html"><div class="but">  SEARCH   </div></a>
				<a href="singin.html"><div class="but">  SIGN IN   </div></a>
				<a href="singout.html"><div class="but">  SIGN UP   </div></a>

				
				
				<div id="poza"> <img src="project23.jpg" width="100px" height="60px" /></div>
				

		 </div>
	<div id="data">
		
		
		 <script>



var mydate=new Date()
var year=mydate.getYear()
if (year < 1000)
year+=1900
var day=mydate.getDay()
var month=mydate.getMonth()+1
if (month<10)
month="0"+month
var daym=mydate.getDate()
if (daym<10)
daym="0"+daym
document.write("<small><font color='000000' face='Arial'><b>"+year+"/"+month+"/"+daym+"</b></font></small>")

</script>

<p align="center"><font face="arial" size="-2"></font><br>
<font face="arial, helvetica" size="-2"><a href="http://javascriptkit.com"></a></font></p> 


	<div id="ceas">
<script type="text/javascript">

new imageclock.display()

</script>
	</div>
		
		</div>
	
		
	
	
	<div class="subbutton"> <h1>  TOP STORIES OF TODAY </h1> </div>
	
	<div id="mygallery" class="stepcarousel">
<div class="belt">

<div class="panel">

	<div class="box"> 
		<div class="casuta"> IMAGE related to the story </div>
		<div class="casutamica">SUMMARY of the story </div>
		
		
	</div>
</div>

<div class="panel">
	<div class="box"> 
	<div class="casuta"> IMAGE related to the story </div>
	<div class="casutamica">SUMMARY of the story </div>

	</div>
</div>

<div class="panel">
	<div class="box"> 
		<div class="casuta"> IMAGE related to the story </div>
		<div class="casutamica">SUMMARY of the story </div>

	</div>
</div>

<div class="panel">
	<div class="box"> 
		<div class="casuta"> IMAGE related to the story </div>
		<div class="casutamica">SUMMARY of the story </div>

	</div>
</div>

<div class="panel">
	<div class="box"> 
		<div class="casuta"> IMAGE related to the story </div>
		<div class="casutamica">SUMMARY of the story </div>

	</div>
</div>



</div>
</div>


<p>
<b></b> <span id="statusA"></span> <b style="margin-left: 30px"></b> <span id="statusC"></span>
</p>

<div id="muie">
<p id="mygallery-paginate">
<span class="paginatecircle" data-moveby="1"></span>
</p>

<p>
<a href="javascript:stepcarousel.stepBy('mygallery', -1)"></a> <a href="javascript:stepcarousel.stepBy('mygallery', 1)" style="margin-left: 80px"></a> <br />

<a href="javascript:stepcarousel.stepTo('mygallery', 1)"></a> <a href="javascript:stepcarousel.stepBy('mygallery', 2)" style="margin-left: 80px"></a>
</p>
	</div>
	
	
	<div id="linie"> </div>
	
	<div id="mare"> 
		<div class="ima"  style="border: 1px solid black "> IMAGE OF THE STORY </div>
		<div class="ima"> SUMMARY OF THE STORY </div>
		<div class="ima" style="border: 1px solid black "> IMAGE OF THE STORY </div>
		<div class="ima"  > SUMMARY OF THE STORY</div>
		<div class="ima" style="border: 1px solid black "> IMAGE OF THE STORY </div>
		<div class="ima"> SUMMARY OF THE STORY</div>
		<div class="ima" style="border: 1px solid black "> IMAGE OF THE STORY </div>
		<div class="ima" > SUMMARY OF THE STORY</div>
		
	</div>
	
	
</body>

</html>
