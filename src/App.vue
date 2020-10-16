<template>
	<div id="app">
		<div class="hero-cookies" :class="{'hero-hide-cookies' : hideCookies}">
			<div class="hero-cookies-wrapper">
				<p class="hero-cookies-caption">
					By accessing and using this website, you acknowledge that you have read and understand our
					<a href="#">Cookie Policy</a>,
					<a href="#">Privacy Policy</a>, and our 
					<a href="#">Term of Services</a>
				</p>
				<button class="hero-cookies-button" @click="hideCookies = true">
					Got It!
				</button>
			</div>
		</div>
		<section class="hero" :class="{'hero-hide-cookies-shift-up' : hideCookies}">
			<div class="hero-wrapper">
				<div class="hero-logo"></div>
				<div class="hero-content">
					<p class="hero-title">Hello! I'm Anom Yulian</p>
					<p class="hero-subtitle">Consult, Design, and Develop Websites</p>
					<p class="hero-caption">
						Have something great in mind? Feel free to contact me. <br>
						I'll help you to make it happens.
					</p>

					<button class="hero-button">LET'S MAKE CONTACT</button>
				</div>
			</div>
		</section>
		<section class="feature">
			<div class="feature-header">
				<p class="feature-header-title">How Can I Help You?</p>
				<p class="feature-header-caption">
					Our work then targeted, best practices outcomes social innovations synergy. <br>
					Venture philianthropy, revolutionary inclusive policymaker relief. User-centered program areas scale.

				</p>
			</div>

			<div class="feature-grid">
				<div class="feature-box">
					<div class="feature-box-wrapper">
						<div class="feature-box-icon">
							<i class="far fa-comments"></i>
						</div>
						<p class="feature-box-title">Consult</p>
						<p class="feature-box-caption">
							Co-create, design thinking; strengthen infrastructure resist granular. Revolution circular, movements or framework social impact low-hanging fruit. Save the world compelling revolutionary progress.

						</p>
						<div class="feature-box-icon"></div>
					</div>
				</div>
				<div class="feature-box">
					<div class="feature-box-wrapper">
						<div class="feature-box-icon">
							<i class="fas fa-paint-brush"></i>
						</div>
						<p class="feature-box-title">Design</p>
						<p class="feature-box-caption">
							Policymaker collaborates collective impact humanitarian shared value vocabulary inspire issue outcomes agile. Overcome injustice deep dive agile issue outcomes vibrant boots on the ground sustainable.
						</p>
						<div class="feature-box-icon"></div>
					</div>
				</div>  
				<div class="feature-box">
					<div class="feature-box-wrapper">
						<div class="feature-box-icon">
							<i class="fas fa-window-restore"></i>
						</div>
						<p class="feature-box-title">Develop</p>
						<p class="feature-box-caption">
							 Revolutionary circular, movements a or impact framework social impact low-hanging. Save the compelling revolutionary inspire progress. Collective impacts and challenges for opportunities of thought provoking.
						</p>
						<div class="feature-box-icon"></div>
					</div>
				</div>
				<div class="feature-box">
					<div class="feature-box-wrapper">
						<div class="feature-box-icon">
							<i class="fas fa-bullhorn"></i>
						</div>
						<p class="feature-box-title">Marketing</p>
						<p class="feature-box-caption">
							Peaceful; vibrant paradigm, collaborative cities. Shared vocabulary agile, replicable, effective altruism youth. Mobilize commitment to overcome injustice resilient, uplift social transparent effective.
						</p>
						<div class="feature-box-icon"></div>
					</div>
				</div>
				<div class="feature-box">
					<div class="feature-box-wrapper">
						<div class="feature-box-icon">
							<i class="fas fa-sliders-h"></i>
						</div>
						<p class="feature-box-title">Manage</p>
						<p class="feature-box-caption">
							Change-makers innovation or shared unit of analysis. Overcome injustice outcomes strategize vibrant boots on the ground sustainable. Optimism, effective altruism invest optimism corporate social.
						</p>
						<div class="feature-box-icon"></div>
					</div>
				</div>
				<div class="feature-box">
					<div class="feature-box-wrapper">
						<div class="feature-box-icon">
							<i class="fas fa-chart-line"></i>
						</div>
						<p class="feature-box-title">Evolve</p>
						<p class="feature-box-caption">
							Activate catalyze and impact contextualize humanitarian. Unit of analysis overcome injustice storytelling altruism. Thought leadership mass incarceration. Outcomes big data, fairness, social game-changer.
						</p>
						<div class="feature-box-icon"></div>
					</div>
				</div>  
			</div>

		</section>
		<section class="footer">
			<p class="footer-caption">© 2020 Anom Yulian. All rights reserved</p>
		</section>
		<section class="newsletter" :class="{'newsletter-shrink' : hideNewsletter}">
			<div class=newsletter-close @click="hideNewsletter = true">&times;</div>
			<p class="newsletter-title">Get latest update in web technologies</p>
			<p class="newsletter-caption">
				I write article related to web tehcnologies, such as design trends, development tools, UI/UX case studies and reviews, and more. Sign up to my newsletter to get them all.
			</p>
			<div class="newsletter-form-wrapper">
				<input 
					class="newsletter-input" 
					type="email" 
					placeholder="Email address">
				<button class="newsletter-button">Count me in!</button>
			</div>
		</section>
	</div>
</template>

<script>

	export default {
		name: 'App',

		data() {
			return {
				hideCookies: false,
				hideNewsletter: true,
			}
		},

		created () {
			window.addEventListener('scroll', this.handleScroll);
		},
		destroyed () {
			window.removeEventListener('scroll', this.handleScroll);
		},
		methods: {
			handleScroll (event) {
				if(window.scrollY > 300 && this.getCookie('hideNewsletter') == '') {
					this.hideNewsletter = false;
					this.createCookie('hideNewsletter', 'true', 10);
				}
			},
			createCookie(name,value,minutes) {
				let expires = '';
				if (minutes) {
					let date = new Date();
					date.setTime(date.getTime()+(minutes*60*1000));
					expires = '; expires='+date.toGMTString();
				} 
				document.cookie = name + "=" + value + expires + "; path=/";
			},
			getCookie(cname) {
				let name = cname + '=';
				let decodedCookie = decodeURIComponent(document.cookie);
				let ca = decodedCookie.split(';');
				for(let i = 0; i <ca.length; i++) {
					let c = ca[i];
					while (c.charAt(0) == ' ') {
						c = c.substring(1);
					}
					if (c.indexOf(name) == 0) {
						return c.substring(name.length, c.length);
					}
				}
				return '';
			}
		},
		

	}

</script>

<style>
body {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	font-size: 14px;
	color: #333;
	background-color: #E5E5E5;
}
a {
	text-decoration: none;
	color:#007bc1;
}
p {
	margin: 0 0 8px;
	line-height: 1.4;
}

</style>

<style scoped>
.hero-cookies {
	position: fixed;
	width: 100%;
	background-color: #E5E5E5;
	padding: 12px 20px;
	transition: all 0.15s;

}
.hero-hide-cookies {
	transform: translate(0, -120px);
	overflow: hidden;
}
.hero-cookies-wrapper {
	display: flex;
	flex-wrap: wrap;
	justify-content: space-between;
	max-width: 720px;
	margin: auto;
}
.hero-cookies-caption {
	margin: 4px 12px 4px 0;
	font-size: 12px;  
	max-width: 620px;
	padding-right: 20px;
	flex: 1;
}
.hero-cookies-button {
	background-color: #007bc1;
	border: none;
	border-radius: 4px;
	color: #fff;
	height: 30px;
	width: 70px;
	cursor: pointer;
	margin-top: 4px;
}
@media only screen and (max-width: 960px) {
	.hero-cookies-caption {
		flex: auto;
	}
}



/* HERO */
.hero {
	background-image: url('./assets/background.jpg');
	background-size: cover;
	background-color: #004a75;
	background-blend-mode: multiply;
	height: 480px;
	margin-top: 70px;
	display: inline-block;
	width: 100%;
	transition: all 0.15s;
}
.hero-hide-cookies-shift-up {
	margin-top: 0;
}
.hero-wrapper {
	height: 100%;
	display: flex;
	flex-direction: column;
}
.hero-logo {
	background-image: url('./assets/logo-white.png');
	background-size: cover;
	height: 50px;
	width: 50px;
	margin-top: 20px;
	margin-left: 40px;

}
.hero-content {
	margin: auto;
	text-align: center;
	margin-top: 80px;
	color: #fff;
}
.hero-title {
	font-size: 28px;
}
.hero-subtitle {
	font-size: 22px;
	font-weight: bold;
}
.hero-button {
	margin-top: 20px;
	background-color: transparent;
	width: 180px;
	padding: 12px 0;
	border: #fff solid 1px;
	color: #fff;
	font-weight: bold;
	font-size: 12px;
	transition: all 0.15s;
}
.hero-button:hover {
	background-color: #fff;
	color: #007bc1;
}
@media only screen and (max-width: 960px) {
	.hero {
		margin-top: 110px;
	}
	.hero-hide-cookies-shift-up {
		margin-top: 0;
	}
}



/* FEATURES */

.feature {
	background-color: #e5e5e5;
	padding: 50px 12px;
}
.feature-header {
	text-align: center;
	margin-bottom: 40px;
}
.feature-header-title {
	font-size: 22px;
}
.feature-grid {
	display: flex;
	flex-wrap: wrap;
	max-width: 1200px;
	margin: auto;
}
.feature-box {
	flex-basis: 33.33%;
}
.feature-box-wrapper {
	margin: 10px 12px;  
	padding: 16px 20px;
	border: 2px groove #fff;
	position: relative;
}
.feature-box-icon {
	position: absolute;
	right: 20px;
	top: 14px;
	font-size: 20px;
	color: #bbb;
}
.feature-box-title {
	font-size: 18px;
}
.feature-box-caption {
	font-size: 12px;
}
@media only screen and (max-width: 960px) {
	.feature-box {
		flex-basis: 50%;
	}
}
@media only screen and (max-width: 480px) {
	.feature-box {
		flex-basis: 100%;
	}
}


/* FOOTER */
.footer {
	background-color: #040325;
	color: #82B8F9;
	font-size: 12px;
	padding: 30px;
	text-align: center;
}



/* NEWSLETTER */

.newsletter {
	position: fixed;
	bottom: 0;
	left: 0;
	background-color: #007bc1de;
	max-width: 640px;
	height: 140px;
	padding: 20px;
	color: #fff;
	transition: all 0.5s;
}
.newsletter-shrink{
	bottom: -40px;	
	height: 0;
}
.newsletter-close {
	text-align: center;
	width: 14px;
	float: right;
	margin-bottom: 33px;
	position: absolute;
	right: 20px;
	top: 8px;
	font-size: 18px;
	cursor: pointer;
}
.newsletter-title {
	font-size: 20px;
}
.newsletter-caption {
	font-size: 12px;
}

.newsletter-form-wrapper {
	display: flex;
	justify-content: space-between;
	flex-wrap: wrap;
}
.newsletter-input {
	width: 100%;
	padding: 8px;
	margin-bottom: 12px;
	border: none;
	border-radius: 2px;
	font-size: 12px;
	font-weight: bold;
	flex: 1;
	margin-right: 12px;
}
.newsletter-button {
	border: none;
	background-color: #ff8000;
	color: #fff;
	padding: 4px 10px;
	border-radius: 2px;
	flex-basis: 20%;
	height: 30px;
	font-size: 12px;
	font-weight: bold;

}

@media only screen and (max-width: 480px) {
	.newsletter {
		height: 160px;
	}
	.newsletter-shrink{
		bottom: -40px;	
		height: 0;
	}
	.newsletter-input {
		margin-right: 0;
	}
	.newsletter-button {
		flex-basis: 100%;
	}
}

</style>
