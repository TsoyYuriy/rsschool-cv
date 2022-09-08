
**Tsoy Yuriy** 

_Kazakhstan, Almaty_

_Phone/WhatsAPP: +77076693747,_
_TG: @Teddy_Green,_
_Discord: Tsoy Yuriy(@TsoyYuriy)_

**About myself**
My goal is to develop as a person, learn new technologies, earn a stable income, and be a sought-after specialist in my field.
Strengths, perseverance, perseverance, patience, curiosity.
I try to spend my free time studying.

**Skills:**
JavaScript, SCSS, SASS, Git, React, HTML, CSS


**Exemple my code:**
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta http-equiv="X-UA-Compatible" content="IE=edge">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<link rel="stylesheet" href="./styles/normalize.css">
	<link rel="stylesheet" href="./styles/style.css">
	<title>homework 34</title>
</head>
<body>

	<div class="container">
		<header class="header">
			<input type="text" class="input">
			<button class="btn-search">Search Country</button>
		</header>

		<main class="main-info">
			<div class="country"></div>
			<div class="city"></div>
		</main>
	
	</div>

	<script>
		const btnSearch = document.querySelector('.btn-search');
		const countryName = document.querySelector('.country');
		const cityName = document.querySelector('.city');
		let necessaryCountry;

		const showOnDisplay = (borderName, city, temp, windDeg, windSpeed) => {
			const pCapital = document.createElement('p');
			pCapital.innerHTML = `${city}, ${temp} temperature, ${windDeg} wind deg, ${windSpeed} km/h`;
			pCapital.classList.add('capital');
			cityName.append(pCapital);

			const span = document.createElement('p');
			span.innerHTML = `${borderName}`
			countryName.append(span)
		}
		
		const weather = async (borderName,city) => {
			const weatherForCapital = await fetch(`http://api.openweathermap.org/geo/1.0/direct?q=${city}&limit=5&appid=e0ee0bdc81fc63dd6330b7d38cf47045`);

			const data = await weatherForCapital.json();
			const lat = data[0].lat;
			const lon = data[0].lon;
			
			const weather = await fetch(`https://api.openweathermap.org/data/2.5/weather?lat=${lat}&lon=${lon}&appid=e0ee0bdc81fc63dd6330b7d38cf47045&lang=ru`);
			const weatherJson = await weather.json();

			const temp = Math.ceil( weatherJson.main.temp - 273.15);
			const windDeg = weatherJson.wind.deg;
			const windSpeed = Math.ceil(weatherJson.wind.speed * 3.6);
			console.log(city, temp + ' temp', windDeg + ' wind',windSpeed + ' wind speed', 12); 
			
			showOnDisplay(borderName, city, temp, windDeg, windSpeed);
		};

		const getInfoCountry = async (nameCountry) => {
			const country = await fetch(`https://restcountries.com/v2/name/${nameCountry}`);
			necessaryCountry = await country.json();
			const necessaryCountryName = necessaryCountry[0].name;
			const necessaryCountryCapital = necessaryCountry[0].capital;
			console.log(necessaryCountryName, necessaryCountryCapital, 2);

			await weather(necessaryCountryName, necessaryCountryCapital);
		};

		const getBorders = async (country) => {
			country.forEach( (el) => {
				try {
					const bordersResp = Promise.all(el.borders.map(async (border) => {
						
						const urlBorders = await fetch(`https://restcountries.com/v2/alpha/${border}`);

						const respBorders = await urlBorders.json();
						const borderName = respBorders.name;
						const borderNameCapital = respBorders.capital;
						console.log(borderName, borderNameCapital, 5);

						await weather(borderName,borderNameCapital);
					}))
				} catch (error) {
					console.log(error);
				}

			})
		};

		const wrapFunc = async (nameCountry) => {
			await getInfoCountry(nameCountry).catch(er => console.log(er));
			getBorders(necessaryCountry);
		}

		btnSearch.addEventListener('click', () => {
			const inputValue = document.querySelector('.input').value;

			if(!inputValue) return;
			countryName.innerHTML = '';
			cityName.innerHTML = '';

			wrapFunc(inputValue);
		})
	</script>
</body>
</html>
```

**Work experience:**
School programming - Attractor School(JavaScript, NodeJS)
(https://tsoyyuriy.github.io/port3/)
(https://tsoyyuriy.github.io/port4/)
(https://tsoyyuriy.github.io/port_5_water_vyatskaya/)

**Education:**
Attractor School(JavaScript, NodeJS)

**English:**
beginner
