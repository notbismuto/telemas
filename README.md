<!DOCTYPE html>
<style>
@font-face {
    font-family: "Monserrat Medium";
    src: url("assets/fonts/monserrat/Montserrat-Medium.ttf") format("truetype");
    font-weight: 0;
}

html,
body {
    margin: 0;
    padding: 0;
    height: 100%;
}

body {
    background-color: rgba(15, 15, 17);
    font-family: "Montserrat Medium", sans-serif;
    color: white;
}

.Header {
    height: 76px;
    width: 100%;
    background-color: rgba(10, 10, 12);
    position: fixed;
    top: 0;
    left: 0;
    border: 1px solid rgba(30, 30, 30);
    display: flex;
    align-items: center;
    padding-left: 10px;
    z-index: 1000;
}

.logo {
    width: 60px;
    margin-left: 10px;
}

.minidivisor {
    width: 2px;
    height: 15px;
    background-color: rgba(238, 240, 255, 0.5);
    margin: 0 15px;
}

.invisibeldivisor {
    width: 2px;
    height: 5px;
    background-color: transparent;
    margin: 5px;
}

.ButtonStyleSelected,
.ButtonStyleIdle {
    display: inline-flex;
    align-items: center;
    height: 30px;
    padding: 0 11px;
    border-radius: 4px;
    border: none;
    font-family: "Montserrat Medium", sans-serif;
    font-weight: 4000;
    cursor: pointer;
}

.ButtonStyleSelected {
    background: rgb(238, 240, 255);
    color: black;
}

.ButtonStyleIdle {
    background: transparent;
    color: white;
}

.Player {
    width: 50%;
    margin: 0 auto;
    margin-top: 5%;
    height: calc(70vh - 75px);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
.ViewboxChildren {
  display: flex;
  flex-direction: column;   

  justify-content: center;  
}

.Frame {
    border-style: solid;
    border-width: 1px;
    border-color: rgb(52, 52, 59);
    width: 190%;
    gap: 20px;
    max-width: 1100px;
    aspect-ratio: 16 / 9;
    background-color: #afafaf;
    border-radius: 8px;
    overflow: hidden;
}

video {
    width: 100%;
    height: 100%;
    object-fit: cover;
    background: black;
}

.CurrentlyViewBox {
  margin-top: 10px;
  display: flex;
  max-width: 900px;
  min-height: 75px;
  width: 95%;
  height: auto;
  margin: 0 auto;
  background-color: rgb(10, 10, 12);
  border: 1px solid rgba(30,30,35);
  border-radius: 8px;
  overflow: hidden; /* clave para que no se rompa el borde */
}

.ViewboxChildren {
  flex: 1; 
    padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  border-right: 1px solid rgba(30,30,35);
}

.ViewboxChildren:last-child {
  border-right: none;
}

.label {
  font-size: 10px;
    text-align: left;
  color: rgba(255,255,255,0.4);
  letter-spacing: 0.5px;
}

.value {
  font-size: 18px;
  font-weight: 500;
  text-align: left;
}

.viewboxActualCGSpan {
    position: absolute;
    margin-top: 25px;
    margin-left: 10px;
    font-family: Gilroy;
    font-size: 35px;
}
.EPGCenter {
    max-width: 90vw;
    max-height: 80vh;
    width: auto;
    height: auto;
    display: block;
    margin: 150px auto 0;
}
</style>
<html lang="es">
  
<head>
  <meta charset="UTF-8">
  <meta property="og:site_name" content="TL+">
  <meta property="og:title" content="En Vivo - TL+">
  <title>En Vivo: TL+</title>
  <meta name="theme-color" content="rgb(238, 240, 255)">
  <meta property="og:image" content="https://media.discordapp.net/attachments/1362078986821435404/1453252682658611200/tlbg.png?ex=694cc687&is=694b7507&hm=872aa192fdb401b222fb170a3d2bef7291295f5c53f7e95b9de7748a6678938b&=&format=webp&quality=lossless&width=1552&height=873">
  <meta name="description" content="TL+ es un canal de televisión salvadoreño dedicado principalmente al contenido generalista, tanto como novelas, películas, animes, etc.">

  <script src="https://cdn.jsdelivr.net/npm/hls.js@latest"></script>
<link rel="stylesheet" href="style.css">
</head>

<body>

  <div class="Header">
    <img src="imgs/TLMAS_BLANCO.png" class="logo">
    <div class="minidivisor"></div>
    <button class="ButtonStyleSelected">EN VIVO</button>
    <div class="invisibeldivisor"></div>
    <button class="ButtonStyleIdle">PROGRAMACION</button>
    <div class="invisibeldivisor"></div>
    <button class="ButtonStyleIdle">NOSOTROS</button>
  </div>
  

  <Button class="ButtonStyleSelected" style="margin: auto() 0;">SEÑAL EN VIVO</Button>
  <div class="Player">
    <div class="Frame">
      <video id="video" autoplay controls></video>
    </div>
  </div>
    <div class="CurrentlyViewBox">
        <span class="viewboxSpan"></span>
    </div>

  <script>
    const video = document.getElementById('video');
    const m3u8 = 'https://cdn.global.elektamedia.com/live/c7eds/TLMasSV/SA_LIVE_hls_enc/master.m3u8';

    if (Hls.isSupported()) {
      const hls = new Hls();
      hls.loadSource(m3u8);
      hls.attachMedia(video);
    } else if (video.canPlayType('application/vnd.apple.mpegurl')) {
      video.src = m3u8;
    }
  </script>

</body>
</html>
