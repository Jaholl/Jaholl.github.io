<script>
let working = true
$: jobbar = working ? "Ja :(" : "NEJ!"
$: src = working ? "" :  "ErikJobbarInte.jpg"
$: jobbarClass = working ? "jobbar" : "jobbarInte"
$: hanSlutar = working ? "Men han slutar om:" : ""
$: timer = ""
setInterval(() => {
	let time = new Date()
	let today = new Date().getDay()
	if (today === 0 || today === 6){
		working = false
	} else if (today === 2 || today === 4){
		if (time.getHours() === 11 ||
			time.getHours() === 12 ||
			time.getHours() === 17){
			working = true
		} else {
			working = false
		}
	} else {
		if (time.getHours() === 11 ||
			time.getHours() === 12){
			working = true
		} else {
			working = false
		}
	}
}, 100);
setInterval(() => {
	let time = new Date()
	let lunchExp = new Date().setHours(13 + time.getTimezoneOffset()/60, 0, 0, 0)
	let kvallsExp = new Date().setHours(18 + time.getTimezoneOffset()/60, 0, 0, 0)
	if (working){
		if (time.getHours() === 11 ||
			time.getHours() === 12){
				let tidKvar = new Date(lunchExp-time)
				timer = tidKvar.getHours() + " timmar, "
				+ tidKvar.getMinutes() + " minuter, "
				+ tidKvar.getSeconds() + " sekunder"
		}
		else
		if (time.getHours() === 17){
				let tidKvar = new Date(kvallsExp-time)
				timer = tidKvar.getHours() + " timmar, "
				+ tidKvar.getMinutes() + " minuter, "
				+ tidKvar.getSeconds() + " sekunder"
		}
	} else {
		timer = ""
	}
}, 100);
</script>

<div>
	<h1>
		<center>
			Jobbar Erik nu?
		</center>
	</h1>
	<div id="jobbar" class="{jobbarClass}">
		<center>
			{jobbar}
		</center>
	</div>
	<div>
		<center>
			{hanSlutar}
			<br/>
			{timer}
		</center>
	</div>
	<img {src} alt=""/>
</div>

<style>
h1 {
	font: 35px 'Trebuchet MS';
	margin-top: 10vh;
}
div{
	display: block;
}
img {
	height: 20em;
	display: flex;
	justify-content: center;
}
.jobbar {
	color: red;
}
.jobbarInte{
	color: green;
}
</style>