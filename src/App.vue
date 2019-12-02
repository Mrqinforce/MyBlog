<template>
	<div id="app"><router-view /></div>
</template>

<script>
export default {
	name: 'App',
	data: () => ({})
};
</script>
<style>
@import url('assets/css/basic.css');
@import url('assets/css/style.css');
#app {
	height: 100%;
	background-image: url(assets/img/7.jpg) ;
	background-size: calc(100%);
}
</style>