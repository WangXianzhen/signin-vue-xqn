<template>
	<ul class="goods">
		<li v-for="good in goods" v-bind:key="good.did">
			<div class="imgs">
				<img v-bind:src="good.image_url">
			</div>
			<div class="information">
				<header>{{good.title}}</header>
				<p class="price">{{good.v_detail}}</p>
				<p class="detail">{{good.editor_rec_desc}}</p>
				<p class="mall">{{good.mall}}</p>
			</div>
		</li>
	</ul>
</template>


<script type="text/javascript">
	export default {
		name: 'goods',
		props: ['goods']
	}
</script>


<style scoped>
ul{
	padding: 0px;
	margin: 0px;
	margin-top: .2rem;
}
li{
	list-style: none;
	overflow: hidden;
	border-top: .01rem solid #f1f1f1;
}
.imgs{
	float: left;
	margin: .25rem;
	margin-left: .05rem;
	width: 2rem;
	height: 2rem;
}
img{
	width: 2rem;
	height: 2rem;
}
.information{
	overflow: hidden;
}
.information header{
	font-size: .26rem;
	height: .6rem;
	line-height: .3rem;
	margin: .25rem 0rem;
}
.price{
	color: red;
	font-size: .28rem;
	margin: 0px;
}
.detail{
	font-size: .28rem;
	color: gray;
	margin: 0px;
}
.mall{
	font-size: .25rem;
	margin: 0px;
	text-align: right;
	color: gray;
}
</style>