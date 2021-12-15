# 解决canvas移动端下滑问题
昨天想着尝试用canvas做一个简易的画板，便写了一个小demo，移动端还是很正常的，到了手机端就发现有一个很难受的现象，手指触摸后，
画的线不能跟着手指走，会超前前进，不受控制，除此外，甚至画布也会随着手指上下移动，哎，总之就是体验感很差。
一开始想的是，明明也已经禁用缩放了，照理来说线应该不会瞎跑呀，后来在思考了一下，划线不受控制应该就是跟画布不能固定，也在上下
移动有关，所以猜测只要画布固定了，那么线就能稳定在手指上了，这样应该就能正常涂鸦了。
要想固定画布，就应该禁止整个页面的滑动，那么就可以用JS来禁止移动端 页面滑动，具体如下：
```
//禁止页面滑动
function stop(e){
      var preMove=function(e){passive: false ;};
      document.body.style.overflow='hidden';
      document.addEventListener("touchmove",preMove,false);//禁止页面滑动
  },
  stop()
//允许页面滑动
function move(e){
      var preMove=function(e){passive: false };
      document.body.style.overflow='';//出现滚动条
      document.removeEventListener("touchmove",preMove,false);
},
``` 
好啦，这下画板完全固定住了，尝试一下，划线也能完全跟着手指，更加流畅了，耶！
