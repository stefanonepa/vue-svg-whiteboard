<template>
	<polygon :points="pointstring" :style="style" ></polygon>
</template>
<script>
	export default{
		props: ['x', 'y', 'size', 'style'],
		computed:{
			points(){
				let siz = this.size;
				//console.log(this.size);
				let pointa = (this.x) + "," + (this.y - siz);
				let pointb = (this.x + siz) + "," + (this.y + siz);
				let pointc = (this.x - siz) + "," + (this.y + siz);
				return {pointa, pointb, pointc};
			},
			pointstring(){
				return `${this.points.pointa} ${this.points.pointb} ${this.points.pointc}`;
			}
		}
	}
</script>