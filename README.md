# Neuromorphic-waves
....html....
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width">
    <title>repl.it</title>
    <link href="style.css" rel="stylesheet" type="text/css" />
  </head>
  <body>
    <script src="script.js"></script>
    <input id="trigger" type="checkbox" hidden>
<label class="trigger" for="trigger"></label>
<div class="dots">
  <div class="dot"></div>
  <div class="dot"></div>
  <div class="dot"></div>
</div>
  </body>
</html>
.....css.....
:root {
  --gray: #eef09a;
  --size: 25vw;
  --scalingFactor: calc(100 / 25); /*related to size*/
}
  
body {
  background: var(--gray);
  margin: 0;
  padding: 0;
  overflow: hidden;
  font-family: sans-serif;
}
.dot, .trigger {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
  height: var(--size);
  width: var(--size);
  margin: 10px;
  background: var(--gray);
  box-shadow: 5px 5px 10px rgba(163, 177, 198, 0.6), -5px -5px 10px rgba(255, 255, 255, 0.5);
  border-radius: 50%;
}
.trigger {
  z-index: 3;
  display: flex;
  align-items: center;
  justify-content: center;
  color: rgba(0,0,0,0.5);
  letter-spacing: 0.05em;
  cursor: pointer;
}
.trigger:before {
  content:'click me'
}
#trigger:checked + .trigger:before {
  content: 'reset'
}

#trigger:checked + .trigger + .dots > .dot {
  animation-name: wave;
  animation-timing-function: ease-in-out;
  animation-duration: 2s;
  animation-fill-mode: forwards;
}
.dot {
  opacity: 1;
  transform: translate3d(-50%,-50%,0) scale3d(0,0,1);
}
.dot:nth-of-type(2) {
  z-index: 1;
  animation-delay: .5s;
}
.dot:nth-of-type(3) {
  z-index: 2;
  animation-delay: 1s;
}

@keyframes wave{
  0% {
    opacity: 1;
    transform: translate3d(-50%,-50%,0) scale3d(1,1,1);
  }  
  100% {
    opacity: 0;
    transform: translate3d(-50%,-50%,0) scale3d(var(--scalingFactor),var(--scalingFactor),1);
  }
}
