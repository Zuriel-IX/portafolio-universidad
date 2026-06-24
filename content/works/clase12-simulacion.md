---
title: 'Simulador de Emprendimiento IT Full Stack - ChatGPT'
order: 12
date: '2026-06-24'
draft: true
---


<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
<style>
main{max-width:1100px;margin:auto;padding:20px}
.card{background:white;padding:20px;margin:15px 0;border-radius:10px;box-shadow:0 2px 6px rgba(0,0,0,.1)}
textarea,input,select{width:100%;padding:10px;margin-top:6px}
button{padding:12px 20px;cursor:pointer}
.progress{height:20px;background:#ddd;border-radius:10px;overflow:hidden}
.bar{height:100%;width:0;background:#22c55e}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:10px}
</style>
</head>
<body>
<p>Basado en Emprendedurismo y Práctica Profesional</p>

<main>
<div class="progress"><div class="bar" id="bar"></div></div>

<div class="card">
<h2>1. Perfil Profesional</h2>
<input id="nombre" placeholder="Nombre del emprendedor">
<select id="perfil">
<option>Frontend</option>
<option>Backend</option>
<option selected>Full Stack</option>
</select>
<textarea id="skills" placeholder="Competencias técnicas y blandas"></textarea>
</div>

<div class="card">
<h2>2. Simulador VICA + MR3</h2>
<p>¿Cómo reaccionarías si una IA vuelve obsoleto parte de tu servicio?</p>
<textarea id="vica"></textarea>
</div>

<div class="card">
<h2>3. Gestión del Tiempo</h2>
<div class="grid">
<textarea id="todo" placeholder="Pendiente"></textarea>
<textarea id="doing" placeholder="En progreso"></textarea>
<textarea id="review" placeholder="En revisión"></textarea>
<textarea id="done" placeholder="Completado"></textarea>
</div>
</div>

<div class="card">
<h2>4. Modelo Profesional</h2>
<select id="modelo">
<option>Consultoría IT</option>
<option>Freelance</option>
<option>SaaS</option>
<option>Agencia</option>
<option>Empleado</option>
</select>
</div>

<div class="card">
<h2>5. Lean Startup</h2>
<textarea id="idea" placeholder="Idea"></textarea>
<textarea id="mvp" placeholder="MVP"></textarea>
<textarea id="aprendizaje" placeholder="Aprendizaje"></textarea>
</div>

<div class="card">
<h2>6. Canvas</h2>
<div class="grid">
<textarea id="clientes" placeholder="Segmentos"></textarea>
<textarea id="valor" placeholder="Propuesta de valor"></textarea>
<textarea id="canales" placeholder="Canales"></textarea>
<textarea id="relacion" placeholder="Relación con clientes"></textarea>
<textarea id="ingresos" placeholder="Ingresos"></textarea>
<textarea id="recursos" placeholder="Recursos"></textarea>
<textarea id="actividades" placeholder="Actividades"></textarea>
<textarea id="socios" placeholder="Socios"></textarea>
<textarea id="costos" placeholder="Costos"></textarea>
</div>
</div>

<div class="card">
<h2>7. Finanzas</h2>
<input type="number" id="inv" placeholder="Inversión inicial">
<input type="number" id="gan" placeholder="Ganancia neta esperada">
<button onclick="calc()">Calcular ROI</button>
<p id="roi"></p>
</div>

<div class="card">
<h2>8. Ética Profesional</h2>
<textarea id="etica" placeholder="¿Qué harías ante un caso de plagio de código?"></textarea>
</div>

<div class="card">
<h2>9. Negociación</h2>
<textarea id="nego" placeholder="Cliente pide funcionalidades extra sin pagar más"></textarea>
</div>

<div class="card">
<h2>10. Licencias</h2>
<select id="licencia">
<option>MIT</option>
<option>GPL</option>
<option>Apache 2.0</option>
<option>BSD</option>
</select>
</div>

<div class="card">
<h2>11. Empresa</h2>
<textarea id="empresa" placeholder="Describe la estructura organizacional"></textarea>
</div>

<div class="card">
<h2>12. Consultoría IT</h2>
<textarea id="servicios" placeholder="Servicios"></textarea>
<textarea id="tecnologias" placeholder="Tecnologías"></textarea>
<textarea id="clientesit" placeholder="Nicho objetivo"></textarea>
</div>

<div class="card">
<button onclick="exportPDF()">Generar PDF Final</button>
</div>

</main>

<script>
function calc(){
 let i=Number(inv.value||0);
 let g=Number(gan.value||0);
 let roi=i?((g/i)*100).toFixed(2):0;
 document.getElementById("roi").innerText="ROI: "+roi+"%";
}

document.addEventListener("input",()=>{
 let total=document.querySelectorAll('textarea,input,select').length;
 let filled=0;
 document.querySelectorAll('textarea,input,select').forEach(e=>{
   if(e.value) filled++;
 });
 document.getElementById("bar").style.width=(filled/total*100)+"%";
});

async function exportPDF(){
 const {jsPDF}=window.jspdf;
 const doc=new jsPDF();
 let y=10;
 doc.setFontSize(18);
 doc.text("Plan de Emprendimiento IT",10,y);
 y+=10;

 document.querySelectorAll("textarea,input,select").forEach(el=>{
   let label=(el.placeholder||el.id||"Campo");
   let text=label+": "+el.value;
   let lines=doc.splitTextToSize(text,180);
   if(y>260){doc.addPage();y=10;}
   doc.text(lines,10,y);
   y+=lines.length*6+4;
 });

 doc.save("emprendimiento_IT.pdf");
}
</script>
</body>
</html>