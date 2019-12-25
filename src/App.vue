<template>
	<div id="app">
		<img alt="Vue logo" src="./assets/logo.png">
		<div v-for="(item,index) in list" :key="index">
			<VueRender :index="index" :row="item.data" :render="item.render"></VueRender>
		</div>
	</div>
</template>

<script>
import VueRender from './components/vueRender'

export default {
	name: 'app',
	components: {
		VueRender
	},
	data() {
		return {
			list: [
				{
					data: {
						name: '科比',
						age: 24
					},
					render: (h, params) => {
						return h('div', [
							h('span', params.row.name),
							h('span', params.row.age)
						])
					}
				},
				{
					data: {
						name: '杜兰特',
						age: 30
					},
					render: (h, params) => {
						return h('div', [
							h('span', { class: 'nameClass' }, params.row.name),
							h('span', { style: { color: 'red' } }, params.row.age)
						])
					}
				}
			]
		}
	}
}
</script>

<style>
#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
	font-size: 16px;
}
.nameClass {
	color: blue;
}
</style>
