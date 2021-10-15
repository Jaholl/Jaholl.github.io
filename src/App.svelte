<script>
let working = true
$: jobbar = working ? "Ja :(" : "NEJ!"
$: src = working ? "" :  "ErikJobbarInte.jpg"
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
</script>

<div>
	<h1>
		<center>
			Jobbar Erik nu?
		</center>
	</h1>
	<div>
		<center>
			{jobbar}
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
</style>