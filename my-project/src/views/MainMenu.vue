<template>
		<nav>
			<div class="main-menu-container">
				<img class="logo" src="PkdexLogo.svg" alt="">
				<div class="grass-poke">
					<img class="random-poke" src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/150.svg" alt="">
					<img class="grass-cover" src="grass4.png" alt="">
				</div>
			</div>
		</nav>
</template>
<script>
export default {
		name: 'MainMenu',
}
</script>
<style lang="css" scoped>
nav{
	width: 100%;
	background: rgba(0,0,0,0.7);
	height: 200px;
}
.logo{
	width: 400px;
	align-self: center;
}
.main-menu-container{
	display: flex;
	width: 80%;
	margin: auto;
	justify-content: space-between;
	margin-bottom: 0;
	align-items: end;
	height: 100%;
}
.grass-poke{
	display: flex;
}
.grass-cover{
	z-index: 10;
}
.random-poke{
	height: 130px;
	position: absolute;
	z-index: 1;
	animation-duration: 7s;
  animation-name: Walk;
  animation-iteration-count: infinite;
  animation-direction: alternate;
	animation-timing-function: ease-in, ease-out;
}
@keyframes Walk {
  from {
    transform: translateX(1px);
  }

  to {
    transform: translateX(700px);
  }
}
.grass-poke > .random-poke:hover{
	transition-duration: 0.7s;
	filter:	opacity(0%); 
}

</style>