<template>
	<view class="container-point">
		<image src="../../static/financing.png" mode="aspectFit" style="width: 100px; height: 100px "></image>
		
		<view class="pointText" style="font-size: 30px !important; ">我的积分</view>
		<view class="pointText">{{point}}</view>
		<button class="custom-btn btn-5"><span>签到</span></button>
		<view> {{text}}</view>
		
	</view>
	
</template>

<script>


export default {
    data() {
        return {
			point:'NULL',
            text: '积分相关活动请联系客服！',
            canAdd: true,
            canRemove: false,
            extraLine: []
        }
		
		
    },
	onLoad() {
		console.log("fetching data");
		this.$store.dispatch('get_UserInfo').then(res=>{
			console.log(res);
			this.point = res.gold;
			
		})
	}
	,
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
    height: 70vh;
	}
	
	.pointText{
		font-size: 100px;
		font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
	}
	
	.custom-btn {
	  width: 130px;
	  height: 80px;
	  color: #fff;
	  border-radius: 5px;
	  padding: 10px 25px;
	  font-family: 'Lato', sans-serif;
	  font-weight: 500;
	  background: transparent;
	  cursor: pointer;
	  transition: all 0.3s ease;
	  position: relative;
	  display: inline-block;
	   box-shadow:inset 2px 2px 2px 0px rgba(255,255,255,.5),
	   7px 7px 20px 0px rgba(0,0,0,.1),
	   4px 4px 5px 0px rgba(0,0,0,.1);
	  outline: none;
	}
	
/* 5 */
.btn-5 {
    width: 130px;
    height: 60px;
    line-height: 42px;
    padding: 0;
    display: flex;
    border: none;
    background: rgb(255,27,0);
    background: linear-gradient(0deg, rgba(255,27,0,1) 0%, rgba(251,75,2,1) 100%);
    justify-content: center;
    align-items: center;
}
.btn-5:hover {
  color: #f0094a;
  background: transparent;
   box-shadow:none;
}
.btn-5:before,
.btn-5:after{
  content:'';
  position:absolute;
  top:0;
  right:0;
  height:2px;
  width:0;
  background: #f0094a;
  box-shadow:
   -1px -1px 5px 0px #fff,
   7px 7px 20px 0px #0003,
   4px 4px 5px 0px #0002;
  transition:400ms ease all;
}
.btn-5:after{
  right:inherit;
  top:inherit;
  left:0;
  bottom:0;
}
.btn-5:hover:before,
.btn-5:hover:after{
  width:200%;
  transition:800ms ease all;
}

</style>
