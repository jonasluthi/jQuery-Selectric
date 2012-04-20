<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>jQuery Selectric</title>
<style type="text/css">
html { font-size: 100%; -webkit-text-size-adjust: 100%; -ms-text-size-adjust: 100%; }
html, button, input, select, textarea { font-family: sans-serif; color: #222; }
body { margin: 0; font-size: 1em; line-height: 1.4; }

::-moz-selection { background: #FF9933; color: #fff; text-shadow: none; }
::selection { background: #FF9933; color: #fff; text-shadow: none; }

/* =============================================================================
   Links
   ========================================================================== */
a { color: #00e; }
a:visited { color: #551a8b; }
a:hover { color: #06e; }
a:focus { outline: thin dotted; }
a:hover, a:active { outline: 0; }

/* =============================================================================
   Typography
   ========================================================================== */
abbr[title] { border-bottom: 1px dotted; }
b, strong { font-weight: bold; }
blockquote { margin: 1em 40px; }
dfn { font-style: italic; }
hr { display: block; height: 1px; border: 0; border-top: 1px solid #ccc; margin: 1em 0; padding: 0; }
ins { background: #ff9; color: #000; text-decoration: none; }
mark { background: #ff0; color: #000; font-style: italic; font-weight: bold; }
pre, code, kbd, samp { font-family: monospace, serif; _font-family: 'courier new', monospace; font-size: 1em; }
pre { white-space: pre; white-space: pre-wrap; word-wrap: break-word; }
q { quotes: none; }
q:before, q:after { content: ""; content: none; }
small { font-size: 85%; }
sub, sup { font-size: 75%; line-height: 0; position: relative; vertical-align: baseline; }
sup { top: -0.5em; }
sub { bottom: -0.25em; }


/* =============================================================================
   Lists
   ========================================================================== */

ul, ol { margin: 1em 0; padding: 0 0 0 40px; }
dd { margin: 0 0 0 40px; }
nav ul, nav ol { list-style: none; list-style-image: none; margin: 0; padding: 0; }

/* =============================================================================
   Embedded content
   ========================================================================== */
img { border: 0; -ms-interpolation-mode: bicubic; vertical-align: middle; }
svg:not(:root) { overflow: hidden; }

/* =============================================================================
   Figures
   ========================================================================== */
figure { margin: 0; }

/* =============================================================================
   Forms
   ========================================================================== */
form { margin: 0; }
fieldset { border: 0; margin: 0; padding: 0; }
label { cursor: pointer; }
legend { border: 0; *margin-left: -7px; padding: 0; white-space: normal; }
button, input, select, textarea { font-size: 100%; margin: 0; vertical-align: baseline; *vertical-align: middle; }
button, input { line-height: normal; }
button, input[type="button"], input[type="reset"], input[type="submit"] { cursor: pointer; -webkit-appearance: button; *overflow: visible; }
button[disabled], input[disabled] { cursor: default; }
input[type="checkbox"], input[type="radio"] { box-sizing: border-box; padding: 0; *width: 13px; *height: 13px; }
input[type="search"] { -webkit-appearance: textfield; -moz-box-sizing: content-box; -webkit-box-sizing: content-box; box-sizing: content-box; }
input[type="search"]::-webkit-search-decoration, input[type="search"]::-webkit-search-cancel-button { -webkit-appearance: none; }
button::-moz-focus-inner, input::-moz-focus-inner { border: 0; padding: 0; }
textarea { overflow: auto; vertical-align: top; resize: vertical; }
input:valid, textarea:valid {  }
input:invalid, textarea:invalid { background-color: #f0dddd; }


/* =============================================================================
   Tables
   ========================================================================== */
table { border-collapse: collapse; border-spacing: 0; }
td { vertical-align: top; }

/* General Styles */
.center { width: 860px; margin: 0 auto; padding: 20px; }
pre { font-size: .8em; border: 1px solid #DDD; background: #FCFCFC; padding: 6px 8px; color: #333; -moz-border-radius: 4px; -webkit-border-radius: 4px; border-radius: 4px; }
table { width: 100%; background: #FCFCFC; }
table td { border: 1px solid #DDD; padding: 6px 8px; }

/* Select */
.selectricWrapper { position: relative; margin: 0 0 10px; }
.selectricWrapper.selectricOpen { z-index: 9999; }
.selectricWrapper select { position: absolute; left: -9999em; }
.selectric { border: 1px solid #CCC; background: #F0F0F0; width: 300px; position: relative; -moz-border-radius: 2px; -webkit-border-radius: 2px; border-radius: 2px; cursor: pointer; line-height: 16px; }
.selectricOpen .selectric { border: 1px solid #999; background: #E8E8E8; z-index: 9999; }
.selectric .label { display: block; white-space: nowrap; overflow: hidden; margin: 0 30px 0 0; padding: 5px 0 5px 5px; font-size: 13px; }
.selectric .label span { background: #09F; color: #FFF; }
.selectric span.button { position: absolute; right: 2px; top: 2px; font-size: 9px; height: 22px; width: 23px; -moz-border-radius: 2px; -webkit-border-radius: 2px; border-radius: 2px; color: #FFF; text-align: center; line-height: 22px; background: #A7C7DC; background: -moz-linear-gradient(top, #A7C7DC 0%, #85B2D3 100%); background: -webkit-gradient(linear, left top, left bottom, color-stop(0%,#A7C7DC), color-stop(100%,#85B2D3)); background: -webkit-linear-gradient(top, #A7C7DC 0%,#85B2D3 100%); background: -o-linear-gradient(top, #A7C7DC 0%,#85B2D3 100%); background: -ms-linear-gradient(top, #A7C7DC 0%,#85B2D3 100%); background: linear-gradient(top, #A7C7DC 0%,#85B2D3 100%); filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#A7C7DC', endColorstr='#85B2D3',GradientType=0 ); }
.hover span.button { border-color: #AAA; background: #85B2D3; }

/* Items box */
.selectricItems ul,
.selectricItems li { list-style: none; padding: 0; margin: 0; }
.selectricItems { display: none; position: absolute; overflow: auto; top: 28px; left: 0; background: #F0F0F0; border: 1px solid #DDD; z-index: 9998; }
.selectricItems li { padding: 5px; cursor: pointer; display: block; border-bottom: 1px solid #DFDFDF; }
.selectricItems li.selected { background: #888; color: #F0F0F0; }
.selectricItems li:hover { background: #999; color: #F0F0F0; }
</style>

</head>
<body>
	<div class="center">
		<h1>jQuery Selectric <span style="font-family:Consolas">Ϟ</span> v1.0</h1>
		
		<p>jQuery Selectric is a jQuery plugin designed to help at stylizing and manipulating HTML selects.</p>
		
		<h2>How to use:</h2>
		
		<p>1. Make sure to include jQuery in your page:</p>
		<pre>&lt;script src=&quot;//ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js&quot;&gt;&lt;/script&gt;</pre>
		
		<p>2. Include <strong>jQuery Selectric:</strong></p>
		<pre>&lt;script src=&quot;js/jquery.selectric.min.js&quot;&gt;&lt;/script&gt;</pre>
		
		<p>3. Put styles in your CSS</p>
		<pre>.selectricWrapper { position: relative; margin: 0 0 10px; }
.selectricWrapper.selectricOpen { z-index: 9999; }
.selectricWrapper select { position: absolute; left: -9999em; }
.selectric { border: 1px solid #CCC; background: #F0F0F0; width: 300px; position: relative; -moz-border-radius: 2px; -webkit-border-radius: 2px; border-radius: 2px; cursor: pointer; line-height: 16px; }
.selectricOpen .selectric { border: 1px solid #999; background: #E8E8E8; z-index: 9999; }
.selectric .label { display: block; white-space: nowrap; overflow: hidden; margin: 0 30px 0 0; padding: 5px 0 5px 5px; font-size: 13px; }
.selectric .label span { background: #09F; color: #FFF; }
.selectric span.button { position: absolute; right: 2px; top: 2px; font-size: 9px; height: 22px; width: 23px; -moz-border-radius: 2px; -webkit-border-radius: 2px; border-radius: 2px; color: #FFF; text-align: center; line-height: 22px; background: #A7C7DC; background: -moz-linear-gradient(top, #A7C7DC 0%, #85B2D3 100%); background: -webkit-gradient(linear, left top, left bottom, color-stop(0%,#A7C7DC), color-stop(100%,#85B2D3)); background: -webkit-linear-gradient(top, #A7C7DC 0%,#85B2D3 100%); background: -o-linear-gradient(top, #A7C7DC 0%,#85B2D3 100%); background: -ms-linear-gradient(top, #A7C7DC 0%,#85B2D3 100%); background: linear-gradient(top, #A7C7DC 0%,#85B2D3 100%); filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#A7C7DC', endColorstr='#85B2D3',GradientType=0 ); }
.hover span.button { border-color: #AAA; background: #85B2D3; }

/* Items box */
.selectricItems ul,
.selectricItems li { list-style: none; padding: 0; margin: 0; }
.selectricItems { display: none; position: absolute; overflow: auto; top: 28px; left: 0; background: #F0F0F0; border: 1px solid #DDD; z-index: 9998; }
.selectricItems li { padding: 5px; cursor: pointer; display: block; border-bottom: 1px solid #DFDFDF; }
.selectricItems li.selected { background: #888; color: #F0F0F0; }
.selectricItems li:hover { background: #999; color: #F0F0F0; }</pre>
		
		<p>4. Initialize <strong>jQuery Selectric:</strong></p>
		<pre>&lt;script&gt;
$(function(){
	$('select').selectric();
});
&lt;/script&gt;</pre>

		<h2>Options:</h2>
		<table>
			<tr>
				<td><strong>Option</strong></td>
				<td><strong>Default</strong></td>
				<td><strong>Type</strong></td>
				<td><strong>Description</strong></td>
			</tr>
			<tr>
				<td>onOpen</td>
				<td>function(){}</td>
				<td>Function</td>
				<td>Function called when select options is opened</td>
			</tr>
			<tr>
				<td>onClose</td>
				<td>function(){}</td>
				<td>Function</td>
				<td>Function called when select options is closed</td>
			</tr>
			<tr>
				<td>maxHeight</td>
				<td>300</td>
				<td>Integer</td>
				<td>Maximum height options box can be</td>
			</tr>
			<tr>
				<td>keySearchTimeout</td>
				<td>500</td>
				<td>Integer</td>
				<td>After this time without pressing any key, the search string is reseted</td>
			</tr>
			<tr>
				<td>highlight</td>
				<td>true</td>
				<td>Boolean</td>
				<td>Highlight searched string in label</td>
			</tr>
			<tr>
				<td>arrowButtonMarkup</td>
				<td>&lt;span class=&quot;button&quot;&gt;&amp;#9660;&lt;/span&gt;</td>
				<td>String [HTML]</td>
				<td>Markup for open options button</td>
			</tr>
			<tr>
				<td>disableOnMobile</td>
				<td>true</td>
				<td>Boolean</td>
				<td>Initialize plugin on mobile browsers</td>
			</tr>
			<tr>
				<td>margin</td>
				<td>5</td>
				<td>Integer</td>
				<td>Minimum space between opened options and window</td>
			</tr>
			<tr>
				<td>bindSufix</td>
				<td>.sl</td>
				<td>String</td>
				<td>Bind events namespace</td>
			</tr>
		</table>

		<h2>Browser support:</h2>
		
		<ul>
			<li>Firefox</li>
			<li>Chrome</li>
			<li>Safari</li>
			<li>Internet Explorer 7+</li>
			<li>Opera</li>
		</ul>
		
		<h2>Demo:</h2>
		
		<select name="countries" id="countries">
			<option value="0">Select with big option Mauris nec orci ut tortor consectetuer dapibus Mauris nec orci ut tortor consectetuer dapibus</option>
			<option value="AF">Afganistán</option>
			<option value="AL">Albania</option>
			<option value="DE">Alemania</option>
			<option value="AD">Andorra</option>
			<option value="AO">Angola</option>
			<option value="AI">Anguilla</option>
			<option value="AQ">Antártida</option>
			<option value="AG">Antigua y Barbuda</option>
			<option value="AN">Antillas Holandesas</option>
			<option value="SA">Arabia Saudí</option>
			<option value="DZ">Argelia</option>
			<option value="AR">Argentina</option>
			<option value="AM">Armenia</option>
			<option value="AW">Aruba</option>
			<option value="AU">Australia</option>
			<option value="AT">Austria</option>
			<option value="AZ">Azerbaiyán</option>
			<option value="BS">Bahamas</option>
			<option value="BH">Bahrein</option>
			<option value="BD">Bangladesh</option>
			<option value="BB">Barbados</option>
			<option value="BE">Bélgica</option>
			<option value="BZ">Belice</option>
			<option value="BJ">Benin</option>
			<option value="BM">Bermudas</option>
			<option value="BY">Bielorrusia</option>
			<option value="MM">Birmania</option>
			<option value="BO">Bolivia</option>
			<option value="BA">Bosnia y Herzegovina</option>
			<option value="BW">Botswana</option>
			<option value="BR">Brasil</option>
			<option value="BN">Brunei</option>
			<option value="BG">Bulgaria</option>
			<option value="BF">Burkina Faso</option>
			<option value="BI">Burundi</option>
			<option value="BT">Bután</option>
			<option value="CV">Cabo Verde</option>
			<option value="KH">Camboya</option>
			<option value="CM">Camerún</option>
			<option value="CA">Canadá</option>
			<option value="TD">Chad</option>
			<option value="CL">Chile</option>
			<option value="CN">China</option>
			<option value="CY">Chipre</option>
			<option value="VA">Ciudad del Vaticano (Santa Sede)</option>
			<option value="CO">Colombia</option>
			<option value="KM">Comores</option>
			<option value="CG">Congo</option>
			<option value="CD">Congo, República Democrática del</option>
			<option value="KR">Corea</option>
			<option value="KP">Corea del Norte</option>
			<option value="CI">Costa de Marfíl</option>
			<option value="CR">Costa Rica</option>
			<option value="HR">Croacia (Hrvatska)</option>
			<option value="CU">Cuba</option>
			<option value="DK">Dinamarca</option>
			<option value="DJ">Djibouti</option>
			<option value="DM">Dominica</option>
			<option value="EC">Ecuador</option>
			<option value="EG">Egipto</option>
			<option value="SV">El Salvador</option>
			<option value="AE">Emiratos Árabes Unidos</option>
			<option value="ER">Eritrea</option>
			<option value="SI">Eslovenia</option>
			<option value="ES">España</option>
			<option value="US">Estados Unidos</option>
			<option value="EE">Estonia</option>
			<option value="ET">Etiopía</option>
			<option value="FJ">Fiji</option>
			<option value="PH">Filipinas</option>
			<option value="FI">Finlandia</option>
			<option value="FR">Francia</option>
			<option value="GA">Gabón</option>
			<option value="GM">Gambia</option>
			<option value="GE">Georgia</option>
			<option value="GH">Ghana</option>
			<option value="GI">Gibraltar</option>
			<option value="GD">Granada</option>
			<option value="GR">Grecia</option>
			<option value="GL">Groenlandia</option>
			<option value="GP">Guadalupe</option>
			<option value="GU">Guam</option>
			<option value="GT">Guatemala</option>
			<option value="GY">Guayana</option>
			<option value="GF">Guayana Francesa</option>
			<option value="GN">Guinea</option>
			<option value="GQ">Guinea Ecuatorial</option>
			<option value="GW">Guinea-Bissau</option>
			<option value="HT">Haití</option>
			<option value="HN">Honduras</option>
			<option value="HU">Hungría</option>
			<option value="IN">India</option>
			<option value="ID">Indonesia</option>
			<option value="IQ">Irak</option>
			<option value="IR">Irán</option>
			<option value="IE">Irlanda</option>
			<option value="BV">Isla Bouvet</option>
			<option value="CX">Isla de Christmas</option>
			<option value="IS">Islandia</option>
			<option value="KY">Islas Caimán</option>
			<option value="CK">Islas Cook</option>
			<option value="CC">Islas de Cocos o Keeling</option>
			<option value="FO">Islas Faroe</option>
			<option value="HM">Islas Heard y McDonald</option>
			<option value="FK">Islas Malvinas</option>
			<option value="MP">Islas Marianas del Norte</option>
			<option value="MH">Islas Marshall</option>
			<option value="UM">Islas menores de Estados Unidos</option>
			<option value="PW">Islas Palau</option>
			<option value="SB">Islas Salomón</option>
			<option value="SJ">Islas Svalbard y Jan Mayen</option>
			<option value="TK">Islas Tokelau</option>
			<option value="TC">Islas Turks y Caicos</option>
			<option value="VI">Islas Vírgenes (EE.UU.)</option>
			<option value="VG">Islas Vírgenes (Reino Unido)</option>
			<option value="WF">Islas Wallis y Futuna</option>
			<option value="IL">Israel</option>
			<option value="IT">Italia</option>
			<option value="JM">Jamaica</option>
			<option value="JP">Japón</option>
			<option value="JO">Jordania</option>
			<option value="KZ">Kazajistán</option>
			<option value="KE">Kenia</option>
			<option value="KG">Kirguizistán</option>
			<option value="KI">Kiribati</option>
			<option value="KW">Kuwait</option>
			<option value="LA">Laos</option>
			<option value="LS">Lesotho</option>
			<option value="LV">Letonia</option>
			<option value="LB">Líbano</option>
			<option value="LR">Liberia</option>
			<option value="LY">Libia</option>
			<option value="LI">Liechtenstein</option>
			<option value="LT">Lituania</option>
			<option value="LU">Luxemburgo</option>
			<option value="MK">Macedonia, Ex-República Yugoslava de</option>
			<option value="MG">Madagascar</option>
			<option value="MY">Malasia</option>
			<option value="MW">Malawi</option>
			<option value="MV">Maldivas</option>
			<option value="ML">Malí</option>
			<option value="MT">Malta</option>
			<option value="MA">Marruecos</option>
			<option value="MQ">Martinica</option>
			<option value="MU">Mauricio</option>
			<option value="MR">Mauritania</option>
			<option value="YT">Mayotte</option>
			<option value="MX">México</option>
			<option value="FM">Micronesia</option>
			<option value="MD">Moldavia</option>
			<option value="MC">Mónaco</option>
			<option value="MN">Mongolia</option>
			<option value="MS">Montserrat</option>
			<option value="MZ">Mozambique</option>
			<option value="NA">Namibia</option>
			<option value="NR">Nauru</option>
			<option value="NP">Nepal</option>
			<option value="NI">Nicaragua</option>
			<option value="NE">Níger</option>
			<option value="NG">Nigeria</option>
			<option value="NU">Niue</option>
			<option value="NF">Norfolk</option>
			<option value="NO">Noruega</option>
			<option value="NC">Nueva Caledonia</option>
			<option value="NZ">Nueva Zelanda</option>
			<option value="OM">Omán</option>
			<option value="NL">Países Bajos</option>
			<option value="PA">Panamá</option>
			<option value="PG">Papúa Nueva Guinea</option>
			<option value="PK">Paquistán</option>
			<option value="PY">Paraguay</option>
			<option value="PE">Perú</option>
			<option value="PN">Pitcairn</option>
			<option value="PF">Polinesia Francesa</option>
			<option value="PL">Polonia</option>
			<option value="PT">Portugal</option>
			<option value="PR">Puerto Rico</option>
			<option value="QA">Qatar</option>
			<option value="UK">Reino Unido</option>
			<option value="CF">República Centroafricana</option>
			<option value="CZ">República Checa</option>
			<option value="ZA">República de Sudáfrica</option>
			<option value="DO">República Dominicana</option>
			<option value="SK">República Eslovaca</option>
			<option value="RE">Reunión</option>
			<option value="RW">Ruanda</option>
			<option value="RO">Rumania</option>
			<option value="RU">Rusia</option>
			<option value="EH">Sahara Occidental</option>
			<option value="KN">Saint Kitts y Nevis</option>
			<option value="WS">Samoa</option>
			<option value="AS">Samoa Americana</option>
			<option value="SM">San Marino</option>
			<option value="VC">San Vicente y Granadinas</option>
			<option value="SH">Santa Helena</option>
			<option value="LC">Santa Lucía</option>
			<option value="ST">Santo Tomé y Príncipe</option>
			<option value="SN">Senegal</option>
			<option value="SC">Seychelles</option>
			<option value="SL">Sierra Leona</option>
			<option value="SG">Singapur</option>
			<option value="SY">Siria</option>
			<option value="SO">Somalia</option>
			<option value="LK">Sri Lanka</option>
			<option value="PM">St. Pierre y Miquelon</option>
			<option value="SZ">Suazilandia</option>
			<option value="SD">Sudán</option>
			<option value="SE">Suecia</option>
			<option value="CH">Suiza</option>
			<option value="SR">Surinam</option>
			<option value="TH">Tailandia</option>
			<option value="TW">Taiwán</option>
			<option value="TZ">Tanzania</option>
			<option value="TJ">Tayikistán</option>
			<option value="TF">Territorios franceses del Sur</option>
			<option value="TP">Timor Oriental</option>
			<option value="TG">Togo</option>
			<option value="TO">Tonga</option>
			<option value="TT">Trinidad y Tobago</option>
			<option value="TN">Túnez</option>
			<option value="TM">Turkmenistán</option>
			<option value="TR">Turquía</option>
			<option value="TV">Tuvalu</option>
			<option value="UA">Ucrania</option>
			<option value="UG">Uganda</option>
			<option value="UY">Uruguay</option>
			<option value="UZ">Uzbekistán</option>
			<option value="VU">Vanuatu</option>
			<option value="VE">Venezuela</option>
			<option value="VN">Vietnam</option>
			<option value="YE">Yemen</option>
			<option value="YU">Yugoslavia</option>
			<option value="ZM">Zambia</option>
			<option value="ZW">Zimbabue</option> 
		</select>
			
		<select>
			<option value="0">Select with few options</option>
			<option value="apple">Apple</option>
			<option value="banana">Banana</option>
		</select>
		
	</div>
	
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js"></script> 
<script>window.jQuery || document.write('<script src="js/jquery.min.js">\x3C/script>')</script> 
<script src="js/jquery.selectric.min.js"></script>
<script>
$(function(){
	$('select').selectric();
});
</script>
</body>
</html>