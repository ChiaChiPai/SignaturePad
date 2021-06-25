<template>
  <h1>
  Draw over image
  </h1>
  <div class="wrapper">
    <img src="https://preview.ibb.co/jnW4Qz/Grumpy_Cat_920x584.jpg" width=400 height=200 />
    <canvas id="signature-pad" class="signature-pad" width=400 height=200></canvas>
  </div>
  <div>
    <button id="save">Save</button>
    <button id="clear">Clear</button>
  </div>
</template>

<script setup>
import { defineProps, ref, onMounted } from "vue";
import SignaturePad from 'signature_pad'

onMounted(() => {
  var signaturePad = new SignaturePad(document.getElementById('signature-pad'), {
    backgroundColor: 'rgba(255, 255, 255, 0)',
    penColor: 'rgb(0, 0, 0)'
  });
  var signaturePad = new SignaturePad(document.getElementById('signature-pad'), {
    backgroundColor: 'rgba(255, 255, 255, 0)',
    penColor: 'rgb(0, 0, 0)'
  });
  
  var saveButton = document.getElementById('save');
  var cancelButton = document.getElementById('clear');
  
  saveButton.addEventListener('click', function (event) {
    var data = signaturePad.toDataURL('image/png');
  
  // Send data to server instead...
    window.open(data);
  });
  
  cancelButton.addEventListener('click', function (event) {
    signaturePad.clear();
  });
})

</script>

<style>
.wrapper {
  position: relative;
  width: 400px;
  height: 200px;
  -moz-user-select: none;
  -webkit-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
img {
  position: absolute;
  left: 0;
  top: 0;
}

.signature-pad {
  position: absolute;
  left: 0;
  top: 0;
  width:400px;
  height:200px;
}
</style>
