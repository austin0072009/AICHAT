<template>
	<view class="container-point">
		<image src="../../static/理财_financing.png" mode="aspectFit" style="width: 100px; height: 100px "></image>
		
		<view class="pointText" style="font-size: 30px !important; ">我的积分</view>
		<view class="pointText">{{point}}</view>
		<view> {{text}}</view>
		
	</view>
</template>

<script>


export default {
    data() {
        return {
			point:'1000',
            text: '积分相关活动请联系客服！',
            canAdd: true,
            canRemove: false,
            extraLine: []
        }
    },
    methods: {
        
    }
}
</script>


<style>
	.container-point{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
    align-content: center;
    flex-wrap: nowrap;
    height: 40vh;
	}
	
	.pointText{
		font-size: 100px;
		font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
	}
</style>
