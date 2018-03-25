#  [video] 
(https://developer.mozilla.org/zh-CN/docs/Web/Guide/HTML/Using_HTML5_audio_and_video)

# autoplay 视频就绪立即播放 

# controls  显示用户控件 播放 音量 下载 

# height / width  设置播放器的宽高

# loop  重复播放

# muted  静音 

# poster  默认显示的图片 

# preload  (auto | metadata | none ) 

 - 页面加载时进行加载 预备播放  如果使用autoplay 则该忽略该属性 

#  src 视频路径 

#   playsinline (true | false) iphone Safari 视频禁止全屏 

#  播放控制  
 ## document.getElementById('demo').play()  播放声音 
 ## document.getElementById('demo').pause() 暂停声音 
 ## document.getElementById('demo').volume+=0.1 提高音量 
 ##  document.getElementById('demo').volume-=0.1 降低音量 
 ## 停止媒体下载  
 -  var mediaElement = document.getElementById("myMediaElementID");
 - mediaElement.pause();
 - mediaElement.src='';
 - mediaElement.removeAttribute("src"); 

 ## 播放时间 

  - var mediaElement = document.getElementById('mediaElementID');
  - mediaElement.seekable.start();  // 返回开始时间 (in seconds)
  - mediaElement.seekable.end();    // 返回结束时间 (in seconds)
  - mediaElement.currentTime = 122; // 设定在 122 seconds
  - mediaElement.played.end();      // 返回浏览器播放的秒数

  ## 播放范围 

 -  http://foo.com/video.mp4#t=10,20
 - 指定视频播放范围为从第10秒到第20秒.
 - http://foo.com/video.mp4#t=,10.5
 - 指定视频从开始播放到第10.5秒.
 - http://foo.com/video.mp4#t=,02:00:00
 - 指定视频从开始播放到两小时.
 - http://foo.com/video.mp4#t=60
 - 指定视频从第60秒播放到结束.

## 使用Flash播放
 ### <video> 标签不被支持时可以使用Flash播放Flash格式的影像
 - <video src="video.ogv" controls>
 -    <object data="flvplayer.swf" type="application/x-shockwave-flash">
 -     <param value="flvplayer.swf" name="movie"/>
 -   </object>
 - </video>


 ## 没有资源可用是显示备用内容
 
 <video controls>
  <source src="dynamicsearch.mp4" type="video/mp4"></source>
  <a href="dynamicsearch.mp4">
    <img src="dynamicsearch.jpg" alt="Dynamic app search in Firefox OS">
  </a>
  <p>Click image to play a video demo of dynamic app search</p>
</video>
 var v = document.querySelector('video'),
    sources = v.querySelectorAll('source'),
    lastsource = sources[sources.length-1];
lastsource.addEventListener('error', function(ev) {
  var d = document.createElement('div');
  d.innerHTML = v.innerHTML;
  v.parentNode.replaceChild(d, v);
}, false);
