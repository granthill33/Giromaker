<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
	<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
	<title>Giromaker: Giro d'Italia '18</title>
	<style>
	  	.submitButtons{
	  		font-size:large;
	  		font-weight: bold;
	  		height:50px;
	  		width:160px;
	  	}

	  	.showButtons{
	  		font-size:x-small;
	  		font-weight: bold;
	  		height:30px;
	  		width:90px;
	  	}

	  	.labels
	  	{
	  		font-weight: bold;
	  	}

	  	.info
	  	{
	  		font-style: italic;
	  	}
	  	
	  	.error
	  	{
	  		font-weight: bold;
	  		color: #FF0000;

	  	}

	  	.links
	  	{
	  		font-size:x-small;

	  	}
	  	.stageNumber
	  	{
	  		font-size:small;
	  		font-weight: bold;
	  	}
	  	.message
	  	{
	  		font-size:small;
	  		font-style: italic;
	  	}

	  	body{
	  		font-family: Open Sans;
	  		font-size: large;
	  	}
	  	br{
	  		line-height:125%;
	  	}
	  	textarea
	  	{
	  		text-align: center;
	  		width: 350px;
	  	}

	</style>
</head>
<body>
<center>
<h1>Giromaker: Giro d'Italia '18</h1>
<br>
<p>Versión 1.0</p>
<br>

<p class="labels">División: &#160
<select id="divisions" onChange="getCredits(); sumPrices(); getRemaining(); printDorsal();">
<option value="0" selected="selected">Selecciona tu división</option>
<option value="2000">Primera división</option>
<option value="1800">Segunda división</option>
<option value="1700">Tercera división</option>
<option value="1600">Cuarta división</option>
<option value="1500">Quinta división</option>
</select></p>
<p class="labels">Usuario:&#160
<input id="user"></input></p>
<table>
	<tr>
		<td align="center" colspan="2"><a class="links" href="https://www.procyclingstats.com/race/giro-d-italia/2018/startlist" target="_blank"><img src="http://www.procyclingstats.com/images/logo_small.jpg" width="49" height="15"> Ver equipos en ProCyclingStats</a></td>
	</tr>
	<tr>
		<td>&#160;</td>
	</tr>
	<tr align="center">
		<td><button class="showButtons" onclick="showProfiles();changeStage(0)">Ver Perfiles</button>
		<button class="showButtons" onclick="showRidersByPrice()">Ciclistas/Precio</button>
		<button class="showButtons" onclick="window.open('normas.html')">Normas</button><td>
	</tr>
	<tr>
		<td>
			<table align="center" id="profiles">
				<tr>
					<td class="message" align="center">(Click en la imagen para ver en tamaño completo)</td>
				</tr>
				<tr>
					<td align="center"><select id="stageNumber" class="stageNumber" onChange="changeStage(value)">
					<option value="0" selected="selected">Selecciona una etapa</option>		
					<option value="1">E1: Jerusalem / Jerusalem (CRI)</option>
					<option value="2">E2: Haifa – Tel Aviv</option>
					<option value="3">E3: Be'er Sheva – Eilat</option>
					<option value="4">E4: Catania – Caltagirone</option>
					<option value="5">E5: Agrigento – Santa Ninfa</option>
					<option value="6">E6: Caltanissetta – Etna</option>
					<option value="7">E7: Pizzo – Praia a Mare</option>
					<option value="8">E8: Praia a Mare - Montevergine</option>
					<option value="9">E9: Pesco Sannita – Gran Sasso d'Italia</option>
					<option value="10">E10: Penne – Gualdo Tadino</option>
					<option value="11">E11: Assisi – Osimo</option>
					<option value="12">E12: Osimo – Imola</option>
					<option value="13">E13: Ferrara – Nervesa della Battaglia</option>
					<option value="14">E14: S.Vito al Tagliamento - Monte Zoncolan</option>
					<option value="15">E15: Tolmezzo – Sappada</option>
					<option value="16">E16: Trento – Rovereto (CRI)</option>
					<option value="17">E17: Riva del Garda – Iseo</option>
					<option value="18">E18: Abbiategrasso – Prato Nevoso</option>
					<option value="19">E19: Venaria Reale – Monte Jafferau</option>
					<option value="20">E20: Susa – Cervinia</option>
					<option value="21">E21: Roma – Roma</option>
					</select></td>
				</tr>
				<tr>
					<td><img src="profiles/Stage1.jpg" id="stages" height="176" width="320" onclick="fullSize()"></td>
				</tr>
			</table>
		</td>
	<tr>
	<tr>
		<td>
			<table align="center" id="ridersByPriceTR">
				<tr>
					<td class="message" align="center">(Solo para visualización, no se incluirá al equipo)</td>
				</tr>
				<tr>
				<br>
				<td align="center"><select>
				<option value="0" selected="selected">Selecciona un corredor</option>
<option value="600" dorsal="181">FROOME Christopher: 600</option>
<option value="475" dorsal="1">DUMOULIN Tom: 475</option>
<option value="375" dorsal="201">ARU Fabio: 375</option>
<option value="375" dorsal="31">LOPEZ Miguel Angel: 375</option>
<option value="375" dorsal="81">PINOT Thibaut: 375</option>
<option value="325" dorsal="111">CHAVES Johan Esteban: 325</option>
<option value="300" dorsal="41">POZZOVIVO Domenico: 300</option>
<option value="300" dorsal="131">VIVIANI Elia: 300</option>
<option value="275" dorsal="118">YATES Simon: 275</option>
<option value="200" dorsal="73">BENNETT Sam: 200</option>
<option value="200" dorsal="141">MEINTJES Louis: 200</option>
<option value="200" dorsal="156">MODOLO Sacha: 200</option>
<option value="200" dorsal="187">POELS Wout: 200</option>
<option value="175" dorsal="172">BENNETT George: 175</option>
<option value="175" dorsal="182">DE LA CRUZ David: 175</option>
<option value="175" dorsal="61">DENNIS Rohan: 175</option>
<option value="175" dorsal="71">FORMOLO Davide: 175</option>
<option value="175" dorsal="208">ULISSI Diego: 175</option>
<option value="175" dorsal="158">WOODS Michael: 175</option>
<option value="150" dorsal="43">BONIFAZIO Niccolo: 150</option>
<option value="150" dorsal="175">GESINK Robert: 150</option>
<option value="150" dorsal="6">OOMEN Sam: 150</option>
<option value="150" dorsal="36">SANCHEZ Luis Leon: 150</option>
<option value="150" dorsal="178">VAN POPPEL Danny: 150</option>
<option value="150" dorsal="101">WELLENS Tim: 150</option>
<option value="125" dorsal="202">ATAPUMA John Darwin: 125</option>
<option value="125" dorsal="191">BRAMBILLA Gianluca: 125</option>
<option value="125" dorsal="105">DEBUSSCHERE Jens: 125</option>
<option value="125" dorsal="11">GENIEZ Alexandre: 125</option>
<option value="125" dorsal="184">HENAO Sergio Luis: 125</option>
<option value="125" dorsal="91">HERMANS Ben: 125</option>
<option value="125" dorsal="34">KANGERT Tanel: 125</option>
<option value="125" dorsal="75">KONRAD Patrick: 125</option>
<option value="125" dorsal="115">KREUZIGER Roman: 125</option>
<option value="125" dorsal="211">MARECZKO Jakub: 125</option>
<option value="125" dorsal="166">MARTIN Tony: 125</option>
<option value="125" dorsal="196">PANTANO Jarlinson: 125</option>
<option value="125" dorsal="207">POLANC Jan: 125</option>
<option value="125" dorsal="86">REICHENBACH Sebasatien: 125</option>
<option value="125" dorsal="65">ROCHE Nicolas: 125</option>
<option value="125" dorsal="66">ROELANDTS Jurgen: 125</option>
<option value="125" dorsal="27">TORRES Rodolfo Andres: 125</option>
<option value="125" dorsal="48">VISCONTI Giovanni: 125</option>
<option value="100" dorsal="142">ANTON Igor: 100</option>
<option value="100" dorsal="171">BATTAGLIN Enrico: 100</option>
<option value="100" dorsal="121">BETANCUR Carlos: 100</option>
<option value="100" dorsal="32">BILBAO Pello: 100</option>
<option value="100" dorsal="122">CARAPAZ Richard: 100</option>
<option value="100" dorsal="24">CATTANEO Mattia: 100</option>
<option value="100" dorsal="51">CICCONE Giulio: 100</option>
<option value="100" dorsal="62">DE MARCHI Alessandro: 100</option>
<option value="100" dorsal="63">DRUCKER Jean-Pierre: 100</option>
<option value="100" dorsal="21">GAVAZZI Francesco: 100</option>
<option value="100" dorsal="144">GIBBONS Ryan: 100</option>
<option value="100" dorsal="54">GUARDINI Andrea: 100</option>
<option value="100" dorsal="113">HAIG Jack: 100</option>
<option value="100" dorsal="33">HIRT Jan: 100</option>
<option value="100" dorsal="44">MOHORIC Matej: 100</option>
<option value="100" dorsal="116">NIEVE Mikel: 100</option>
<option value="100" dorsal="146">O'CONNOR Ben: 100</option>
<option value="100" dorsal="97">SBARAGLI Kristian: 100</option>
<option value="100" dorsal="47">SIUTSOU Kanstantsin: 100</option>
<option value="75" dorsal="102">ARMÉE Sander: 75</option>
<option value="75" dorsal="22">BALLERINI Davide: 75</option>
<option value="75" dorsal="53">BARBIN Enrico: 75</option>
<option value="75" dorsal="23">BELLETTI Manuel: 75</option>
<option value="75" dorsal="143">BERHANE Natnael: 75</option>
<option value="75" dorsal="173">BOUWMAN Koen: 75</option>
<option value="75" dorsal="104">CAMPENAERTS Victor: 75</option>
<option value="75" dorsal="153">CARTHY Hugh: 75</option>
<option value="75" dorsal="133">CAVAGNA Rémi: 75</option>
<option value="75" dorsal="13">CHÉREL Mickaël: 75</option>
<option value="75" dorsal="155">DOMBROWSKI Joe: 75</option>
<option value="75" dorsal="162">DOWSETT Alex: 75</option>
<option value="75" dorsal="15">DUPONT Hubert: 75</option>
<option value="75" dorsal="193">EG Niklas: 75</option>
<option value="75" dorsal="183">ELISSONDE Kenny: 75</option>
<option value="75" dorsal="124">FERNÁNDEZ Rubén: 75</option>
<option value="75" dorsal="64">FRANKINY Kilian: 75</option>
<option value="75" dorsal="163">GONÇALVES José: 75</option>
<option value="75" dorsal="74">GROSSSCHARTNER Felix: 75</option>
<option value="75" dorsal="147">JANSE VAN RENSBURG Jacques: 75</option>
<option value="75" dorsal="185">KIRYIENKA Vasil: 75</option>
<option value="75" dorsal="35">LUTSENKO Alexey: 75</option>
<option value="75" dorsal="26">MASNADA Fausto: 75</option>
<option value="75" dorsal="17">MONTAGUTI Matteo: 75</option>
<option value="75" dorsal="134">MØRKØV Michael: 75</option>
<option value="75" dorsal="215">MOSCA Jacopo: 75</option>
<option value="75" dorsal="195">MULLEN Ryan: 75</option>
<option value="75" dorsal="94">NEILANDS Krists: 75</option>
<option value="75" dorsal="197">PEDERSEN Mads: 75</option>
<option value="75" dorsal="167">PLANCKAERT Baptiste: 75</option>
<option value="75" dorsal="96">PLAZA Rubén: 75</option>
<option value="75" dorsal="85">PREIDLER Georg: 75</option>
<option value="75" dorsal="136">SCHACHMANN Maximilian: 75</option>
<option value="75" dorsal="77">SELIG Rüdiger: 75</option>
<option value="75" dorsal="127">SEPÚLVEDA Eduardo: 75</option>
<option value="75" dorsal="138">STYBAR Zdenek : 75</option>
<option value="75" dorsal="7">TEN DAM Laurens: 75</option>
<option value="75" dorsal="128">VALLS Rafael: 75</option>
<option value="75" dorsal="157">VAN ASBROECK Tom: 75</option>
<option value="75" dorsal="108">VAN DER SANDE Tosh: 75</option>
<option value="75" dorsal="174">VAN EMDEN Jos: 75</option>
<option value="75" dorsal="198">VAN POPPEL Boy: 75</option>
<option value="75" dorsal="18">VENTURINI Clément: 75</option>
<option value="75" dorsal="8">VERVAEKE Louis: 75</option>
<option value="75" dorsal="37">VILLELLA Davide: 75</option>
<option value="50" dorsal="52">ANDREETTA Simone: 50</option>
<option value="50" dorsal="103">BAK Lars Ytting: 50</option>
<option value="50" dorsal="161">BELKOV Maxim: 50</option>
<option value="50" dorsal="72">BENEDETTI Cesare: 50</option>
<option value="50" dorsal="212">BERTAZZO Liam: 50</option>
<option value="50" dorsal="112">BEWLEY Sam: 50</option>
<option value="50" dorsal="12">BIDARD François: 50</option>
<option value="50" dorsal="42">BOARO Manuele: 50</option>
<option value="50" dorsal="92">BOIVIN Guillaume: 50</option>
<option value="50" dorsal="82">BONNET William: 50</option>
<option value="50" dorsal="151">BROWN Nathan: 50</option>
<option value="50" dorsal="132">CAPECCHI Eros: 50</option>
<option value="50" dorsal="213">COLEDAN Marco: 50</option>
<option value="50" dorsal="203">CONTI Valerio: 50</option>
<option value="50" dorsal="2">CURVERS Roy: 50</option>
<option value="50" dorsal="123">DE LA PARTE Víctor: 50</option>
<option value="50" dorsal="93">DEMPSTER Zakkari: 50</option>
<option value="50" dorsal="14">DENZ Nico: 50</option>
<option value="50" dorsal="192">DIDIER Laurent: 50</option>
<option value="50" dorsal="154">DOCKER Mitchell: 50</option>
<option value="50" dorsal="214">FONZI Giuseppe: 50</option>
<option value="50" dorsal="25">FRAPPORTI Marco: 50</option>
<option value="50" dorsal="106">FRISON Frederik: 50</option>
<option value="50" dorsal="3">HAGA Chad: 50</option>
<option value="50" dorsal="4">HAMILTON Chris: 50</option>
<option value="50" dorsal="107">HANSEN Adam: 50</option>
<option value="50" dorsal="5">HOFSTEDE Lennard: 50</option>
<option value="50" dorsal="194">IRIZAR Markel: 50</option>
<option value="50" dorsal="16">JAUREGUI Quentin: 50</option>
<option value="50" dorsal="114">JUUL-JENSEN Christopher: 50</option>
<option value="50" dorsal="145">KING Benjamin: 50</option>
<option value="50" dorsal="186">KNEES Christian: 50</option>
<option value="50" dorsal="164">KUZNETSOV Viacheslav: 50</option>
<option value="50" dorsal="83">LADAGNOUS Matthieu: 50</option>
<option value="50" dorsal="204">LAENGEN Vegard Stake : 50</option>
<option value="50" dorsal="165">LAMMERTINK Maurits: 50</option>
<option value="50" dorsal="177">LINDEMAN Bert-Jan: 50</option>
<option value="50" dorsal="55">MAESTRI Mirco: 50</option>
<option value="50" dorsal="205">MARCATO Marco: 50</option>
<option value="50" dorsal="84">MORABITO Steve: 50</option>
<option value="50" dorsal="206">MORI Manuele: 50</option>
<option value="50" dorsal="45">NIBALI Antonio: 50</option>
<option value="50" dorsal="95">NIV Guy: 50</option>
<option value="50" dorsal="46">NOVAK Domen: 50</option>
<option value="50" dorsal="125">PEDRERO Antonio: 50</option>
<option value="50" dorsal="76">PFINGSTEN Christoph: 50</option>
<option value="50" dorsal="188">PUCCIO Salvatore: 50</option>
<option value="50" dorsal="126">QUINTANA Dayer: 50</option>
<option value="50" dorsal="87">ROUX Anthony: 50</option>
<option value="50" dorsal="88">ROY Jeremy: 50</option>
<option value="50" dorsal="135">SABATINI Fabio: 50</option>
<option value="50" dorsal="98">SAGIV Guy: 50</option>
<option value="50" dorsal="78">SCHILLINGER Andreas: 50</option>
<option value="50" dorsal="152">SCULLY Thomas: 50</option>
<option value="50" dorsal="137">SÉNÉCHAL Florian: 50</option>
<option value="50" dorsal="56">SENNI Manuel: 50</option>
<option value="50" dorsal="57">SIMION Paolo: 50</option>
<option value="50" dorsal="58">TONELLI Alessandro: 50</option>
<option value="50" dorsal="117">TUFT Svein: 50</option>
<option value="50" dorsal="216">TURRIN Alex: 50</option>
<option value="50" dorsal="176">VAN HOECKE Gijs: 50</option>
<option value="50" dorsal="28">VENDRAME Andrea: 50</option>
<option value="50" dorsal="148">VENTER Jaco: 50</option>
<option value="50" dorsal="67">VENTOSO Francisco : 50</option>
<option value="50" dorsal="68">VLIEGEN Loïc: 50</option>
<option value="50" dorsal="168">WÜRTZ SCHMIDT Mads: 50</option>
<option value="50" dorsal="217">ZARDINI Edoardo: 50</option>
<option value="50" dorsal="38">ZEITS Andrey: 50</option>
<option value="50" dorsal="218">ZHUPA Eugert: 50</option></select></td>
			</tr>
			</table>
		</td>
	<tr>
		<td class="labels">Presupuesto:&#160&#160</td>
		<td id="budget">0</td>
	</tr>
	<tr>
		<td class="labels">Presupuesto restante:&#160&#160</td>
		<td id="remainingBudget">0</td>	
	</tr>
	<tr>
		<td align="center" colspan="2" class="error" id="error"></td>
	</tr>
</table>
<br>
<table>
	<tr>
		<td class="labels">C1 :&#160</td>
<td><select id="rider1" onChange="getCredits(); sumPrices(); getRemaining(); printDorsal();">
<option value="0" selected="selected">Selecciona un corredor</option>
<option value="50" dorsal="52">ANDREETTA Simone: 50</option>
<option value="100" dorsal="142">ANTON Igor: 100</option>
<option value="75" dorsal="102">ARMÉE Sander: 75</option>
<option value="375" dorsal="201">ARU Fabio: 375</option>
<option value="125" dorsal="202">ATAPUMA John Darwin: 125</option>
<option value="50" dorsal="103">BAK Lars Ytting: 50</option>
<option value="75" dorsal="22">BALLERINI Davide: 75</option>
<option value="75" dorsal="53">BARBIN Enrico: 75</option>
<option value="100" dorsal="171">BATTAGLIN Enrico: 100</option>
<option value="50" dorsal="161">BELKOV Maxim: 50</option>
<option value="75" dorsal="23">BELLETTI Manuel: 75</option>
<option value="50" dorsal="72">BENEDETTI Cesare: 50</option>
<option value="175" dorsal="172">BENNETT George: 175</option>
<option value="200" dorsal="73">BENNETT Sam: 200</option>
<option value="75" dorsal="143">BERHANE Natnael: 75</option>
<option value="50" dorsal="212">BERTAZZO Liam: 50</option>
<option value="100" dorsal="121">BETANCUR Carlos: 100</option>
<option value="50" dorsal="112">BEWLEY Sam: 50</option>
<option value="50" dorsal="12">BIDARD François: 50</option>
<option value="100" dorsal="32">BILBAO Pello: 100</option>
<option value="50" dorsal="42">BOARO Manuele: 50</option>
<option value="50" dorsal="92">BOIVIN Guillaume: 50</option>
<option value="150" dorsal="43">BONIFAZIO Niccolo: 150</option>
<option value="50" dorsal="82">BONNET William: 50</option>
<option value="75" dorsal="173">BOUWMAN Koen: 75</option>
<option value="125" dorsal="191">BRAMBILLA Gianluca: 125</option>
<option value="50" dorsal="151">BROWN Nathan: 50</option>
<option value="75" dorsal="104">CAMPENAERTS Victor: 75</option>
<option value="50" dorsal="132">CAPECCHI Eros: 50</option>
<option value="100" dorsal="122">CARAPAZ Richard: 100</option>
<option value="75" dorsal="153">CARTHY Hugh: 75</option>
<option value="100" dorsal="24">CATTANEO Mattia: 100</option>
<option value="75" dorsal="133">CAVAGNA Rémi: 75</option>
<option value="325" dorsal="111">CHAVES Johan Esteban: 325</option>
<option value="75" dorsal="13">CHÉREL Mickaël: 75</option>
<option value="100" dorsal="51">CICCONE Giulio: 100</option>
<option value="50" dorsal="213">COLEDAN Marco: 50</option>
<option value="50" dorsal="203">CONTI Valerio: 50</option>
<option value="50" dorsal="2">CURVERS Roy: 50</option>
<option value="175" dorsal="182">DE LA CRUZ David: 175</option>
<option value="50" dorsal="123">DE LA PARTE Víctor: 50</option>
<option value="100" dorsal="62">DE MARCHI Alessandro: 100</option>
<option value="125" dorsal="105">DEBUSSCHERE Jens: 125</option>
<option value="50" dorsal="93">DEMPSTER Zakkari: 50</option>
<option value="175" dorsal="61">DENNIS Rohan: 175</option>
<option value="50" dorsal="14">DENZ Nico: 50</option>
<option value="50" dorsal="192">DIDIER Laurent: 50</option>
<option value="50" dorsal="154">DOCKER Mitchell: 50</option>
<option value="75" dorsal="155">DOMBROWSKI Joe: 75</option>
<option value="75" dorsal="162">DOWSETT Alex: 75</option>
<option value="100" dorsal="63">DRUCKER Jean-Pierre: 100</option>
<option value="475" dorsal="1">DUMOULIN Tom: 475</option>
<option value="75" dorsal="15">DUPONT Hubert: 75</option>
<option value="75" dorsal="193">EG Niklas: 75</option>
<option value="75" dorsal="183">ELISSONDE Kenny: 75</option>
<option value="75" dorsal="124">FERNÁNDEZ Rubén: 75</option>
<option value="50" dorsal="214">FONZI Giuseppe: 50</option>
<option value="175" dorsal="71">FORMOLO Davide: 175</option>
<option value="75" dorsal="64">FRANKINY Kilian: 75</option>
<option value="50" dorsal="25">FRAPPORTI Marco: 50</option>
<option value="50" dorsal="106">FRISON Frederik: 50</option>
<option value="600" dorsal="181">FROOME Christopher: 600</option>
<option value="100" dorsal="21">GAVAZZI Francesco: 100</option>
<option value="125" dorsal="11">GENIEZ Alexandre: 125</option>
<option value="150" dorsal="175">GESINK Robert: 150</option>
<option value="100" dorsal="144">GIBBONS Ryan: 100</option>
<option value="75" dorsal="163">GONÇALVES José: 75</option>
<option value="75" dorsal="74">GROSSSCHARTNER Felix: 75</option>
<option value="100" dorsal="54">GUARDINI Andrea: 100</option>
<option value="50" dorsal="3">HAGA Chad: 50</option>
<option value="100" dorsal="113">HAIG Jack: 100</option>
<option value="50" dorsal="4">HAMILTON Chris: 50</option>
<option value="50" dorsal="107">HANSEN Adam: 50</option>
<option value="125" dorsal="184">HENAO Sergio Luis: 125</option>
<option value="125" dorsal="91">HERMANS Ben: 125</option>
<option value="100" dorsal="33">HIRT Jan: 100</option>
<option value="50" dorsal="5">HOFSTEDE Lennard: 50</option>
<option value="50" dorsal="194">IRIZAR Markel: 50</option>
<option value="75" dorsal="147">JANSE VAN RENSBURG Jacques: 75</option>
<option value="50" dorsal="16">JAUREGUI Quentin: 50</option>
<option value="50" dorsal="114">JUUL-JENSEN Christopher: 50</option>
<option value="125" dorsal="34">KANGERT Tanel: 125</option>
<option value="50" dorsal="145">KING Benjamin: 50</option>
<option value="75" dorsal="185">KIRYIENKA Vasil: 75</option>
<option value="50" dorsal="186">KNEES Christian: 50</option>
<option value="125" dorsal="75">KONRAD Patrick: 125</option>
<option value="125" dorsal="115">KREUZIGER Roman: 125</option>
<option value="50" dorsal="164">KUZNETSOV Viacheslav: 50</option>
<option value="50" dorsal="83">LADAGNOUS Matthieu: 50</option>
<option value="50" dorsal="204">LAENGEN Vegard Stake : 50</option>
<option value="50" dorsal="165">LAMMERTINK Maurits: 50</option>
<option value="50" dorsal="177">LINDEMAN Bert-Jan: 50</option>
<option value="375" dorsal="31">LOPEZ Miguel Angel: 375</option>
<option value="75" dorsal="35">LUTSENKO Alexey: 75</option>
<option value="50" dorsal="55">MAESTRI Mirco: 50</option>
<option value="50" dorsal="205">MARCATO Marco: 50</option>
<option value="125" dorsal="211">MARECZKO Jakub: 125</option>
<option value="125" dorsal="166">MARTIN Tony: 125</option>
<option value="75" dorsal="26">MASNADA Fausto: 75</option>
<option value="200" dorsal="141">MEINTJES Louis: 200</option>
<option value="200" dorsal="156">MODOLO Sacha: 200</option>
<option value="100" dorsal="44">MOHORIC Matej: 100</option>
<option value="75" dorsal="17">MONTAGUTI Matteo: 75</option>
<option value="50" dorsal="84">MORABITO Steve: 50</option>
<option value="50" dorsal="206">MORI Manuele: 50</option>
<option value="75" dorsal="134">MØRKØV Michael: 75</option>
<option value="75" dorsal="215">MOSCA Jacopo: 75</option>
<option value="75" dorsal="195">MULLEN Ryan: 75</option>
<option value="75" dorsal="94">NEILANDS Krists: 75</option>
<option value="50" dorsal="45">NIBALI Antonio: 50</option>
<option value="100" dorsal="116">NIEVE Mikel: 100</option>
<option value="50" dorsal="95">NIV Guy: 50</option>
<option value="50" dorsal="46">NOVAK Domen: 50</option>
<option value="100" dorsal="146">O'CONNOR Ben: 100</option>
<option value="150" dorsal="6">OOMEN Sam: 150</option>
<option value="125" dorsal="196">PANTANO Jarlinson: 125</option>
<option value="75" dorsal="197">PEDERSEN Mads: 75</option>
<option value="50" dorsal="125">PEDRERO Antonio: 50</option>
<option value="50" dorsal="76">PFINGSTEN Christoph: 50</option>
<option value="375" dorsal="81">PINOT Thibaut: 375</option>
<option value="75" dorsal="167">PLANCKAERT Baptiste: 75</option>
<option value="75" dorsal="96">PLAZA Rubén: 75</option>
<option value="200" dorsal="187">POELS Wout: 200</option>
<option value="125" dorsal="207">POLANC Jan: 125</option>
<option value="300" dorsal="41">POZZOVIVO Domenico: 300</option>
<option value="75" dorsal="85">PREIDLER Georg: 75</option>
<option value="50" dorsal="188">PUCCIO Salvatore: 50</option>
<option value="50" dorsal="126">QUINTANA Dayer: 50</option>
<option value="125" dorsal="86">REICHENBACH Sebasatien: 125</option>
<option value="125" dorsal="65">ROCHE Nicolas: 125</option>
<option value="125" dorsal="66">ROELANDTS Jurgen: 125</option>
<option value="50" dorsal="87">ROUX Anthony: 50</option>
<option value="50" dorsal="88">ROY Jeremy: 50</option>
<option value="50" dorsal="135">SABATINI Fabio: 50</option>
<option value="50" dorsal="98">SAGIV Guy: 50</option>
<option value="150" dorsal="36">SANCHEZ Luis Leon: 150</option>
<option value="100" dorsal="97">SBARAGLI Kristian: 100</option>
<option value="75" dorsal="136">SCHACHMANN Maximilian: 75</option>
<option value="50" dorsal="78">SCHILLINGER Andreas: 50</option>
<option value="50" dorsal="152">SCULLY Thomas: 50</option>
<option value="75" dorsal="77">SELIG Rüdiger: 75</option>
<option value="50" dorsal="137">SÉNÉCHAL Florian: 50</option>
<option value="50" dorsal="56">SENNI Manuel: 50</option>
<option value="75" dorsal="127">SEPÚLVEDA Eduardo: 75</option>
<option value="50" dorsal="57">SIMION Paolo: 50</option>
<option value="100" dorsal="47">SIUTSOU Kanstantsin: 100</option>
<option value="75" dorsal="138">STYBAR Zdenek : 75</option>
<option value="75" dorsal="7">TEN DAM Laurens: 75</option>
<option value="50" dorsal="58">TONELLI Alessandro: 50</option>
<option value="125" dorsal="27">TORRES Rodolfo Andres: 125</option>
<option value="50" dorsal="117">TUFT Svein: 50</option>
<option value="50" dorsal="216">TURRIN Alex: 50</option>
<option value="175" dorsal="208">ULISSI Diego: 175</option>
<option value="75" dorsal="128">VALLS Rafael: 75</option>
<option value="75" dorsal="157">VAN ASBROECK Tom: 75</option>
<option value="75" dorsal="108">VAN DER SANDE Tosh: 75</option>
<option value="75" dorsal="174">VAN EMDEN Jos: 75</option>
<option value="50" dorsal="176">VAN HOECKE Gijs: 50</option>
<option value="75" dorsal="198">VAN POPPEL Boy: 75</option>
<option value="150" dorsal="178">VAN POPPEL Danny: 150</option>
<option value="50" dorsal="28">VENDRAME Andrea: 50</option>
<option value="50" dorsal="148">VENTER Jaco: 50</option>
<option value="50" dorsal="67">VENTOSO Francisco : 50</option>
<option value="75" dorsal="18">VENTURINI Clément: 75</option>
<option value="75" dorsal="8">VERVAEKE Louis: 75</option>
<option value="75" dorsal="37">VILLELLA Davide: 75</option>
<option value="125" dorsal="48">VISCONTI Giovanni: 125</option>
<option value="300" dorsal="131">VIVIANI Elia: 300</option>
<option value="50" dorsal="68">VLIEGEN Loïc: 50</option>
<option value="150" dorsal="101">WELLENS Tim: 150</option>
<option value="175" dorsal="158">WOODS Michael: 175</option>
<option value="50" dorsal="168">WÜRTZ SCHMIDT Mads: 50</option>
<option value="275" dorsal="118">YATES Simon: 275</option>
<option value="50" dorsal="217">ZARDINI Edoardo: 50</option>
<option value="50" dorsal="38">ZEITS Andrey: 50</option>
<option value="50" dorsal="218">ZHUPA Eugert: 50</option>
</tr><tr>
<td class="labels">C2 :&#160</td>
<td><select id="rider2" onChange="getCredits(); sumPrices(); getRemaining(); printDorsal();">
<option value="0" selected="selected">Selecciona un corredor</option>
<option value="50" dorsal="52">ANDREETTA Simone: 50</option>
<option value="100" dorsal="142">ANTON Igor: 100</option>
<option value="75" dorsal="102">ARMÉE Sander: 75</option>
<option value="375" dorsal="201">ARU Fabio: 375</option>
<option value="125" dorsal="202">ATAPUMA John Darwin: 125</option>
<option value="50" dorsal="103">BAK Lars Ytting: 50</option>
<option value="75" dorsal="22">BALLERINI Davide: 75</option>
<option value="75" dorsal="53">BARBIN Enrico: 75</option>
<option value="100" dorsal="171">BATTAGLIN Enrico: 100</option>
<option value="50" dorsal="161">BELKOV Maxim: 50</option>
<option value="75" dorsal="23">BELLETTI Manuel: 75</option>
<option value="50" dorsal="72">BENEDETTI Cesare: 50</option>
<option value="175" dorsal="172">BENNETT George: 175</option>
<option value="200" dorsal="73">BENNETT Sam: 200</option>
<option value="75" dorsal="143">BERHANE Natnael: 75</option>
<option value="50" dorsal="212">BERTAZZO Liam: 50</option>
<option value="100" dorsal="121">BETANCUR Carlos: 100</option>
<option value="50" dorsal="112">BEWLEY Sam: 50</option>
<option value="50" dorsal="12">BIDARD François: 50</option>
<option value="100" dorsal="32">BILBAO Pello: 100</option>
<option value="50" dorsal="42">BOARO Manuele: 50</option>
<option value="50" dorsal="92">BOIVIN Guillaume: 50</option>
<option value="150" dorsal="43">BONIFAZIO Niccolo: 150</option>
<option value="50" dorsal="82">BONNET William: 50</option>
<option value="75" dorsal="173">BOUWMAN Koen: 75</option>
<option value="125" dorsal="191">BRAMBILLA Gianluca: 125</option>
<option value="50" dorsal="151">BROWN Nathan: 50</option>
<option value="75" dorsal="104">CAMPENAERTS Victor: 75</option>
<option value="50" dorsal="132">CAPECCHI Eros: 50</option>
<option value="100" dorsal="122">CARAPAZ Richard: 100</option>
<option value="75" dorsal="153">CARTHY Hugh: 75</option>
<option value="100" dorsal="24">CATTANEO Mattia: 100</option>
<option value="75" dorsal="133">CAVAGNA Rémi: 75</option>
<option value="325" dorsal="111">CHAVES Johan Esteban: 325</option>
<option value="75" dorsal="13">CHÉREL Mickaël: 75</option>
<option value="100" dorsal="51">CICCONE Giulio: 100</option>
<option value="50" dorsal="213">COLEDAN Marco: 50</option>
<option value="50" dorsal="203">CONTI Valerio: 50</option>
<option value="50" dorsal="2">CURVERS Roy: 50</option>
<option value="175" dorsal="182">DE LA CRUZ David: 175</option>
<option value="50" dorsal="123">DE LA PARTE Víctor: 50</option>
<option value="100" dorsal="62">DE MARCHI Alessandro: 100</option>
<option value="125" dorsal="105">DEBUSSCHERE Jens: 125</option>
<option value="50" dorsal="93">DEMPSTER Zakkari: 50</option>
<option value="175" dorsal="61">DENNIS Rohan: 175</option>
<option value="50" dorsal="14">DENZ Nico: 50</option>
<option value="50" dorsal="192">DIDIER Laurent: 50</option>
<option value="50" dorsal="154">DOCKER Mitchell: 50</option>
<option value="75" dorsal="155">DOMBROWSKI Joe: 75</option>
<option value="75" dorsal="162">DOWSETT Alex: 75</option>
<option value="100" dorsal="63">DRUCKER Jean-Pierre: 100</option>
<option value="475" dorsal="1">DUMOULIN Tom: 475</option>
<option value="75" dorsal="15">DUPONT Hubert: 75</option>
<option value="75" dorsal="193">EG Niklas: 75</option>
<option value="75" dorsal="183">ELISSONDE Kenny: 75</option>
<option value="75" dorsal="124">FERNÁNDEZ Rubén: 75</option>
<option value="50" dorsal="214">FONZI Giuseppe: 50</option>
<option value="175" dorsal="71">FORMOLO Davide: 175</option>
<option value="75" dorsal="64">FRANKINY Kilian: 75</option>
<option value="50" dorsal="25">FRAPPORTI Marco: 50</option>
<option value="50" dorsal="106">FRISON Frederik: 50</option>
<option value="600" dorsal="181">FROOME Christopher: 600</option>
<option value="100" dorsal="21">GAVAZZI Francesco: 100</option>
<option value="125" dorsal="11">GENIEZ Alexandre: 125</option>
<option value="150" dorsal="175">GESINK Robert: 150</option>
<option value="100" dorsal="144">GIBBONS Ryan: 100</option>
<option value="75" dorsal="163">GONÇALVES José: 75</option>
<option value="75" dorsal="74">GROSSSCHARTNER Felix: 75</option>
<option value="100" dorsal="54">GUARDINI Andrea: 100</option>
<option value="50" dorsal="3">HAGA Chad: 50</option>
<option value="100" dorsal="113">HAIG Jack: 100</option>
<option value="50" dorsal="4">HAMILTON Chris: 50</option>
<option value="50" dorsal="107">HANSEN Adam: 50</option>
<option value="125" dorsal="184">HENAO Sergio Luis: 125</option>
<option value="125" dorsal="91">HERMANS Ben: 125</option>
<option value="100" dorsal="33">HIRT Jan: 100</option>
<option value="50" dorsal="5">HOFSTEDE Lennard: 50</option>
<option value="50" dorsal="194">IRIZAR Markel: 50</option>
<option value="75" dorsal="147">JANSE VAN RENSBURG Jacques: 75</option>
<option value="50" dorsal="16">JAUREGUI Quentin: 50</option>
<option value="50" dorsal="114">JUUL-JENSEN Christopher: 50</option>
<option value="125" dorsal="34">KANGERT Tanel: 125</option>
<option value="50" dorsal="145">KING Benjamin: 50</option>
<option value="75" dorsal="185">KIRYIENKA Vasil: 75</option>
<option value="50" dorsal="186">KNEES Christian: 50</option>
<option value="125" dorsal="75">KONRAD Patrick: 125</option>
<option value="125" dorsal="115">KREUZIGER Roman: 125</option>
<option value="50" dorsal="164">KUZNETSOV Viacheslav: 50</option>
<option value="50" dorsal="83">LADAGNOUS Matthieu: 50</option>
<option value="50" dorsal="204">LAENGEN Vegard Stake : 50</option>
<option value="50" dorsal="165">LAMMERTINK Maurits: 50</option>
<option value="50" dorsal="177">LINDEMAN Bert-Jan: 50</option>
<option value="375" dorsal="31">LOPEZ Miguel Angel: 375</option>
<option value="75" dorsal="35">LUTSENKO Alexey: 75</option>
<option value="50" dorsal="55">MAESTRI Mirco: 50</option>
<option value="50" dorsal="205">MARCATO Marco: 50</option>
<option value="125" dorsal="211">MARECZKO Jakub: 125</option>
<option value="125" dorsal="166">MARTIN Tony: 125</option>
<option value="75" dorsal="26">MASNADA Fausto: 75</option>
<option value="200" dorsal="141">MEINTJES Louis: 200</option>
<option value="200" dorsal="156">MODOLO Sacha: 200</option>
<option value="100" dorsal="44">MOHORIC Matej: 100</option>
<option value="75" dorsal="17">MONTAGUTI Matteo: 75</option>
<option value="50" dorsal="84">MORABITO Steve: 50</option>
<option value="50" dorsal="206">MORI Manuele: 50</option>
<option value="75" dorsal="134">MØRKØV Michael: 75</option>
<option value="75" dorsal="215">MOSCA Jacopo: 75</option>
<option value="75" dorsal="195">MULLEN Ryan: 75</option>
<option value="75" dorsal="94">NEILANDS Krists: 75</option>
<option value="50" dorsal="45">NIBALI Antonio: 50</option>
<option value="100" dorsal="116">NIEVE Mikel: 100</option>
<option value="50" dorsal="95">NIV Guy: 50</option>
<option value="50" dorsal="46">NOVAK Domen: 50</option>
<option value="100" dorsal="146">O'CONNOR Ben: 100</option>
<option value="150" dorsal="6">OOMEN Sam: 150</option>
<option value="125" dorsal="196">PANTANO Jarlinson: 125</option>
<option value="75" dorsal="197">PEDERSEN Mads: 75</option>
<option value="50" dorsal="125">PEDRERO Antonio: 50</option>
<option value="50" dorsal="76">PFINGSTEN Christoph: 50</option>
<option value="375" dorsal="81">PINOT Thibaut: 375</option>
<option value="75" dorsal="167">PLANCKAERT Baptiste: 75</option>
<option value="75" dorsal="96">PLAZA Rubén: 75</option>
<option value="200" dorsal="187">POELS Wout: 200</option>
<option value="125" dorsal="207">POLANC Jan: 125</option>
<option value="300" dorsal="41">POZZOVIVO Domenico: 300</option>
<option value="75" dorsal="85">PREIDLER Georg: 75</option>
<option value="50" dorsal="188">PUCCIO Salvatore: 50</option>
<option value="50" dorsal="126">QUINTANA Dayer: 50</option>
<option value="125" dorsal="86">REICHENBACH Sebasatien: 125</option>
<option value="125" dorsal="65">ROCHE Nicolas: 125</option>
<option value="125" dorsal="66">ROELANDTS Jurgen: 125</option>
<option value="50" dorsal="87">ROUX Anthony: 50</option>
<option value="50" dorsal="88">ROY Jeremy: 50</option>
<option value="50" dorsal="135">SABATINI Fabio: 50</option>
<option value="50" dorsal="98">SAGIV Guy: 50</option>
<option value="150" dorsal="36">SANCHEZ Luis Leon: 150</option>
<option value="100" dorsal="97">SBARAGLI Kristian: 100</option>
<option value="75" dorsal="136">SCHACHMANN Maximilian: 75</option>
<option value="50" dorsal="78">SCHILLINGER Andreas: 50</option>
<option value="50" dorsal="152">SCULLY Thomas: 50</option>
<option value="75" dorsal="77">SELIG Rüdiger: 75</option>
<option value="50" dorsal="137">SÉNÉCHAL Florian: 50</option>
<option value="50" dorsal="56">SENNI Manuel: 50</option>
<option value="75" dorsal="127">SEPÚLVEDA Eduardo: 75</option>
<option value="50" dorsal="57">SIMION Paolo: 50</option>
<option value="100" dorsal="47">SIUTSOU Kanstantsin: 100</option>
<option value="75" dorsal="138">STYBAR Zdenek : 75</option>
<option value="75" dorsal="7">TEN DAM Laurens: 75</option>
<option value="50" dorsal="58">TONELLI Alessandro: 50</option>
<option value="125" dorsal="27">TORRES Rodolfo Andres: 125</option>
<option value="50" dorsal="117">TUFT Svein: 50</option>
<option value="50" dorsal="216">TURRIN Alex: 50</option>
<option value="175" dorsal="208">ULISSI Diego: 175</option>
<option value="75" dorsal="128">VALLS Rafael: 75</option>
<option value="75" dorsal="157">VAN ASBROECK Tom: 75</option>
<option value="75" dorsal="108">VAN DER SANDE Tosh: 75</option>
<option value="75" dorsal="174">VAN EMDEN Jos: 75</option>
<option value="50" dorsal="176">VAN HOECKE Gijs: 50</option>
<option value="75" dorsal="198">VAN POPPEL Boy: 75</option>
<option value="150" dorsal="178">VAN POPPEL Danny: 150</option>
<option value="50" dorsal="28">VENDRAME Andrea: 50</option>
<option value="50" dorsal="148">VENTER Jaco: 50</option>
<option value="50" dorsal="67">VENTOSO Francisco : 50</option>
<option value="75" dorsal="18">VENTURINI Clément: 75</option>
<option value="75" dorsal="8">VERVAEKE Louis: 75</option>
<option value="75" dorsal="37">VILLELLA Davide: 75</option>
<option value="125" dorsal="48">VISCONTI Giovanni: 125</option>
<option value="300" dorsal="131">VIVIANI Elia: 300</option>
<option value="50" dorsal="68">VLIEGEN Loïc: 50</option>
<option value="150" dorsal="101">WELLENS Tim: 150</option>
<option value="175" dorsal="158">WOODS Michael: 175</option>
<option value="50" dorsal="168">WÜRTZ SCHMIDT Mads: 50</option>
<option value="275" dorsal="118">YATES Simon: 275</option>
<option value="50" dorsal="217">ZARDINI Edoardo: 50</option>
<option value="50" dorsal="38">ZEITS Andrey: 50</option>
<option value="50" dorsal="218">ZHUPA Eugert: 50</option>
</tr><tr>
<td class="labels">C3 :&#160</td>
<td><select id="rider3" onChange="getCredits(); sumPrices(); getRemaining(); printDorsal();">
<option value="0" selected="selected">Selecciona un corredor</option>
<option value="50" dorsal="52">ANDREETTA Simone: 50</option>
<option value="100" dorsal="142">ANTON Igor: 100</option>
<option value="75" dorsal="102">ARMÉE Sander: 75</option>
<option value="375" dorsal="201">ARU Fabio: 375</option>
<option value="125" dorsal="202">ATAPUMA John Darwin: 125</option>
<option value="50" dorsal="103">BAK Lars Ytting: 50</option>
<option value="75" dorsal="22">BALLERINI Davide: 75</option>
<option value="75" dorsal="53">BARBIN Enrico: 75</option>
<option value="100" dorsal="171">BATTAGLIN Enrico: 100</option>
<option value="50" dorsal="161">BELKOV Maxim: 50</option>
<option value="75" dorsal="23">BELLETTI Manuel: 75</option>
<option value="50" dorsal="72">BENEDETTI Cesare: 50</option>
<option value="175" dorsal="172">BENNETT George: 175</option>
<option value="200" dorsal="73">BENNETT Sam: 200</option>
<option value="75" dorsal="143">BERHANE Natnael: 75</option>
<option value="50" dorsal="212">BERTAZZO Liam: 50</option>
<option value="100" dorsal="121">BETANCUR Carlos: 100</option>
<option value="50" dorsal="112">BEWLEY Sam: 50</option>
<option value="50" dorsal="12">BIDARD François: 50</option>
<option value="100" dorsal="32">BILBAO Pello: 100</option>
<option value="50" dorsal="42">BOARO Manuele: 50</option>
<option value="50" dorsal="92">BOIVIN Guillaume: 50</option>
<option value="150" dorsal="43">BONIFAZIO Niccolo: 150</option>
<option value="50" dorsal="82">BONNET William: 50</option>
<option value="75" dorsal="173">BOUWMAN Koen: 75</option>
<option value="125" dorsal="191">BRAMBILLA Gianluca: 125</option>
<option value="50" dorsal="151">BROWN Nathan: 50</option>
<option value="75" dorsal="104">CAMPENAERTS Victor: 75</option>
<option value="50" dorsal="132">CAPECCHI Eros: 50</option>
<option value="100" dorsal="122">CARAPAZ Richard: 100</option>
<option value="75" dorsal="153">CARTHY Hugh: 75</option>
<option value="100" dorsal="24">CATTANEO Mattia: 100</option>
<option value="75" dorsal="133">CAVAGNA Rémi: 75</option>
<option value="325" dorsal="111">CHAVES Johan Esteban: 325</option>
<option value="75" dorsal="13">CHÉREL Mickaël: 75</option>
<option value="100" dorsal="51">CICCONE Giulio: 100</option>
<option value="50" dorsal="213">COLEDAN Marco: 50</option>
<option value="50" dorsal="203">CONTI Valerio: 50</option>
<option value="50" dorsal="2">CURVERS Roy: 50</option>
<option value="175" dorsal="182">DE LA CRUZ David: 175</option>
<option value="50" dorsal="123">DE LA PARTE Víctor: 50</option>
<option value="100" dorsal="62">DE MARCHI Alessandro: 100</option>
<option value="125" dorsal="105">DEBUSSCHERE Jens: 125</option>
<option value="50" dorsal="93">DEMPSTER Zakkari: 50</option>
<option value="175" dorsal="61">DENNIS Rohan: 175</option>
<option value="50" dorsal="14">DENZ Nico: 50</option>
<option value="50" dorsal="192">DIDIER Laurent: 50</option>
<option value="50" dorsal="154">DOCKER Mitchell: 50</option>
<option value="75" dorsal="155">DOMBROWSKI Joe: 75</option>
<option value="75" dorsal="162">DOWSETT Alex: 75</option>
<option value="100" dorsal="63">DRUCKER Jean-Pierre: 100</option>
<option value="475" dorsal="1">DUMOULIN Tom: 475</option>
<option value="75" dorsal="15">DUPONT Hubert: 75</option>
<option value="75" dorsal="193">EG Niklas: 75</option>
<option value="75" dorsal="183">ELISSONDE Kenny: 75</option>
<option value="75" dorsal="124">FERNÁNDEZ Rubén: 75</option>
<option value="50" dorsal="214">FONZI Giuseppe: 50</option>
<option value="175" dorsal="71">FORMOLO Davide: 175</option>
<option value="75" dorsal="64">FRANKINY Kilian: 75</option>
<option value="50" dorsal="25">FRAPPORTI Marco: 50</option>
<option value="50" dorsal="106">FRISON Frederik: 50</option>
<option value="600" dorsal="181">FROOME Christopher: 600</option>
<option value="100" dorsal="21">GAVAZZI Francesco: 100</option>
<option value="125" dorsal="11">GENIEZ Alexandre: 125</option>
<option value="150" dorsal="175">GESINK Robert: 150</option>
<option value="100" dorsal="144">GIBBONS Ryan: 100</option>
<option value="75" dorsal="163">GONÇALVES José: 75</option>
<option value="75" dorsal="74">GROSSSCHARTNER Felix: 75</option>
<option value="100" dorsal="54">GUARDINI Andrea: 100</option>
<option value="50" dorsal="3">HAGA Chad: 50</option>
<option value="100" dorsal="113">HAIG Jack: 100</option>
<option value="50" dorsal="4">HAMILTON Chris: 50</option>
<option value="50" dorsal="107">HANSEN Adam: 50</option>
<option value="125" dorsal="184">HENAO Sergio Luis: 125</option>
<option value="125" dorsal="91">HERMANS Ben: 125</option>
<option value="100" dorsal="33">HIRT Jan: 100</option>
<option value="50" dorsal="5">HOFSTEDE Lennard: 50</option>
<option value="50" dorsal="194">IRIZAR Markel: 50</option>
<option value="75" dorsal="147">JANSE VAN RENSBURG Jacques: 75</option>
<option value="50" dorsal="16">JAUREGUI Quentin: 50</option>
<option value="50" dorsal="114">JUUL-JENSEN Christopher: 50</option>
<option value="125" dorsal="34">KANGERT Tanel: 125</option>
<option value="50" dorsal="145">KING Benjamin: 50</option>
<option value="75" dorsal="185">KIRYIENKA Vasil: 75</option>
<option value="50" dorsal="186">KNEES Christian: 50</option>
<option value="125" dorsal="75">KONRAD Patrick: 125</option>
<option value="125" dorsal="115">KREUZIGER Roman: 125</option>
<option value="50" dorsal="164">KUZNETSOV Viacheslav: 50</option>
<option value="50" dorsal="83">LADAGNOUS Matthieu: 50</option>
<option value="50" dorsal="204">LAENGEN Vegard Stake : 50</option>
<option value="50" dorsal="165">LAMMERTINK Maurits: 50</option>
<option value="50" dorsal="177">LINDEMAN Bert-Jan: 50</option>
<option value="375" dorsal="31">LOPEZ Miguel Angel: 375</option>
<option value="75" dorsal="35">LUTSENKO Alexey: 75</option>
<option value="50" dorsal="55">MAESTRI Mirco: 50</option>
<option value="50" dorsal="205">MARCATO Marco: 50</option>
<option value="125" dorsal="211">MARECZKO Jakub: 125</option>
<option value="125" dorsal="166">MARTIN Tony: 125</option>
<option value="75" dorsal="26">MASNADA Fausto: 75</option>
<option value="200" dorsal="141">MEINTJES Louis: 200</option>
<option value="200" dorsal="156">MODOLO Sacha: 200</option>
<option value="100" dorsal="44">MOHORIC Matej: 100</option>
<option value="75" dorsal="17">MONTAGUTI Matteo: 75</option>
<option value="50" dorsal="84">MORABITO Steve: 50</option>
<option value="50" dorsal="206">MORI Manuele: 50</option>
<option value="75" dorsal="134">MØRKØV Michael: 75</option>
<option value="75" dorsal="215">MOSCA Jacopo: 75</option>
<option value="75" dorsal="195">MULLEN Ryan: 75</option>
<option value="75" dorsal="94">NEILANDS Krists: 75</option>
<option value="50" dorsal="45">NIBALI Antonio: 50</option>
<option value="100" dorsal="116">NIEVE Mikel: 100</option>
<option value="50" dorsal="95">NIV Guy: 50</option>
<option value="50" dorsal="46">NOVAK Domen: 50</option>
<option value="100" dorsal="146">O'CONNOR Ben: 100</option>
<option value="150" dorsal="6">OOMEN Sam: 150</option>
<option value="125" dorsal="196">PANTANO Jarlinson: 125</option>
<option value="75" dorsal="197">PEDERSEN Mads: 75</option>
<option value="50" dorsal="125">PEDRERO Antonio: 50</option>
<option value="50" dorsal="76">PFINGSTEN Christoph: 50</option>
<option value="375" dorsal="81">PINOT Thibaut: 375</option>
<option value="75" dorsal="167">PLANCKAERT Baptiste: 75</option>
<option value="75" dorsal="96">PLAZA Rubén: 75</option>
<option value="200" dorsal="187">POELS Wout: 200</option>
<option value="125" dorsal="207">POLANC Jan: 125</option>
<option value="300" dorsal="41">POZZOVIVO Domenico: 300</option>
<option value="75" dorsal="85">PREIDLER Georg: 75</option>
<option value="50" dorsal="188">PUCCIO Salvatore: 50</option>
<option value="50" dorsal="126">QUINTANA Dayer: 50</option>
<option value="125" dorsal="86">REICHENBACH Sebasatien: 125</option>
<option value="125" dorsal="65">ROCHE Nicolas: 125</option>
<option value="125" dorsal="66">ROELANDTS Jurgen: 125</option>
<option value="50" dorsal="87">ROUX Anthony: 50</option>
<option value="50" dorsal="88">ROY Jeremy: 50</option>
<option value="50" dorsal="135">SABATINI Fabio: 50</option>
<option value="50" dorsal="98">SAGIV Guy: 50</option>
<option value="150" dorsal="36">SANCHEZ Luis Leon: 150</option>
<option value="100" dorsal="97">SBARAGLI Kristian: 100</option>
<option value="75" dorsal="136">SCHACHMANN Maximilian: 75</option>
<option value="50" dorsal="78">SCHILLINGER Andreas: 50</option>
<option value="50" dorsal="152">SCULLY Thomas: 50</option>
<option value="75" dorsal="77">SELIG Rüdiger: 75</option>
<option value="50" dorsal="137">SÉNÉCHAL Florian: 50</option>
<option value="50" dorsal="56">SENNI Manuel: 50</option>
<option value="75" dorsal="127">SEPÚLVEDA Eduardo: 75</option>
<option value="50" dorsal="57">SIMION Paolo: 50</option>
<option value="100" dorsal="47">SIUTSOU Kanstantsin: 100</option>
<option value="75" dorsal="138">STYBAR Zdenek : 75</option>
<option value="75" dorsal="7">TEN DAM Laurens: 75</option>
<option value="50" dorsal="58">TONELLI Alessandro: 50</option>
<option value="125" dorsal="27">TORRES Rodolfo Andres: 125</option>
<option value="50" dorsal="117">TUFT Svein: 50</option>
<option value="50" dorsal="216">TURRIN Alex: 50</option>
<option value="175" dorsal="208">ULISSI Diego: 175</option>
<option value="75" dorsal="128">VALLS Rafael: 75</option>
<option value="75" dorsal="157">VAN ASBROECK Tom: 75</option>
<option value="75" dorsal="108">VAN DER SANDE Tosh: 75</option>
<option value="75" dorsal="174">VAN EMDEN Jos: 75</option>
<option value="50" dorsal="176">VAN HOECKE Gijs: 50</option>
<option value="75" dorsal="198">VAN POPPEL Boy: 75</option>
<option value="150" dorsal="178">VAN POPPEL Danny: 150</option>
<option value="50" dorsal="28">VENDRAME Andrea: 50</option>
<option value="50" dorsal="148">VENTER Jaco: 50</option>
<option value="50" dorsal="67">VENTOSO Francisco : 50</option>
<option value="75" dorsal="18">VENTURINI Clément: 75</option>
<option value="75" dorsal="8">VERVAEKE Louis: 75</option>
<option value="75" dorsal="37">VILLELLA Davide: 75</option>
<option value="125" dorsal="48">VISCONTI Giovanni: 125</option>
<option value="300" dorsal="131">VIVIANI Elia: 300</option>
<option value="50" dorsal="68">VLIEGEN Loïc: 50</option>
<option value="150" dorsal="101">WELLENS Tim: 150</option>
<option value="175" dorsal="158">WOODS Michael: 175</option>
<option value="50" dorsal="168">WÜRTZ SCHMIDT Mads: 50</option>
<option value="275" dorsal="118">YATES Simon: 275</option>
<option value="50" dorsal="217">ZARDINI Edoardo: 50</option>
<option value="50" dorsal="38">ZEITS Andrey: 50</option>
<option value="50" dorsal="218">ZHUPA Eugert: 50</option>
</tr><tr>
<td class="labels">C4 :&#160</td>
<td><select id="rider4" onChange="getCredits(); sumPrices(); getRemaining(); printDorsal();">
<option value="0" selected="selected">Selecciona un corredor</option>
<option value="50" dorsal="52">ANDREETTA Simone: 50</option>
<option value="100" dorsal="142">ANTON Igor: 100</option>
<option value="75" dorsal="102">ARMÉE Sander: 75</option>
<option value="375" dorsal="201">ARU Fabio: 375</option>
<option value="125" dorsal="202">ATAPUMA John Darwin: 125</option>
<option value="50" dorsal="103">BAK Lars Ytting: 50</option>
<option value="75" dorsal="22">BALLERINI Davide: 75</option>
<option value="75" dorsal="53">BARBIN Enrico: 75</option>
<option value="100" dorsal="171">BATTAGLIN Enrico: 100</option>
<option value="50" dorsal="161">BELKOV Maxim: 50</option>
<option value="75" dorsal="23">BELLETTI Manuel: 75</option>
<option value="50" dorsal="72">BENEDETTI Cesare: 50</option>
<option value="175" dorsal="172">BENNETT George: 175</option>
<option value="200" dorsal="73">BENNETT Sam: 200</option>
<option value="75" dorsal="143">BERHANE Natnael: 75</option>
<option value="50" dorsal="212">BERTAZZO Liam: 50</option>
<option value="100" dorsal="121">BETANCUR Carlos: 100</option>
<option value="50" dorsal="112">BEWLEY Sam: 50</option>
<option value="50" dorsal="12">BIDARD François: 50</option>
<option value="100" dorsal="32">BILBAO Pello: 100</option>
<option value="50" dorsal="42">BOARO Manuele: 50</option>
<option value="50" dorsal="92">BOIVIN Guillaume: 50</option>
<option value="150" dorsal="43">BONIFAZIO Niccolo: 150</option>
<option value="50" dorsal="82">BONNET William: 50</option>
<option value="75" dorsal="173">BOUWMAN Koen: 75</option>
<option value="125" dorsal="191">BRAMBILLA Gianluca: 125</option>
<option value="50" dorsal="151">BROWN Nathan: 50</option>
<option value="75" dorsal="104">CAMPENAERTS Victor: 75</option>
<option value="50" dorsal="132">CAPECCHI Eros: 50</option>
<option value="100" dorsal="122">CARAPAZ Richard: 100</option>
<option value="75" dorsal="153">CARTHY Hugh: 75</option>
<option value="100" dorsal="24">CATTANEO Mattia: 100</option>
<option value="75" dorsal="133">CAVAGNA Rémi: 75</option>
<option value="325" dorsal="111">CHAVES Johan Esteban: 325</option>
<option value="75" dorsal="13">CHÉREL Mickaël: 75</option>
<option value="100" dorsal="51">CICCONE Giulio: 100</option>
<option value="50" dorsal="213">COLEDAN Marco: 50</option>
<option value="50" dorsal="203">CONTI Valerio: 50</option>
<option value="50" dorsal="2">CURVERS Roy: 50</option>
<option value="175" dorsal="182">DE LA CRUZ David: 175</option>
<option value="50" dorsal="123">DE LA PARTE Víctor: 50</option>
<option value="100" dorsal="62">DE MARCHI Alessandro: 100</option>
<option value="125" dorsal="105">DEBUSSCHERE Jens: 125</option>
<option value="50" dorsal="93">DEMPSTER Zakkari: 50</option>
<option value="175" dorsal="61">DENNIS Rohan: 175</option>
<option value="50" dorsal="14">DENZ Nico: 50</option>
<option value="50" dorsal="192">DIDIER Laurent: 50</option>
<option value="50" dorsal="154">DOCKER Mitchell: 50</option>
<option value="75" dorsal="155">DOMBROWSKI Joe: 75</option>
<option value="75" dorsal="162">DOWSETT Alex: 75</option>
<option value="100" dorsal="63">DRUCKER Jean-Pierre: 100</option>
<option value="475" dorsal="1">DUMOULIN Tom: 475</option>
<option value="75" dorsal="15">DUPONT Hubert: 75</option>
<option value="75" dorsal="193">EG Niklas: 75</option>
<option value="75" dorsal="183">ELISSONDE Kenny: 75</option>
<option value="75" dorsal="124">FERNÁNDEZ Rubén: 75</option>
<option value="50" dorsal="214">FONZI Giuseppe: 50</option>
<option value="175" dorsal="71">FORMOLO Davide: 175</option>
<option value="75" dorsal="64">FRANKINY Kilian: 75</option>
<option value="50" dorsal="25">FRAPPORTI Marco: 50</option>
<option value="50" dorsal="106">FRISON Frederik: 50</option>
<option value="600" dorsal="181">FROOME Christopher: 600</option>
<option value="100" dorsal="21">GAVAZZI Francesco: 100</option>
<option value="125" dorsal="11">GENIEZ Alexandre: 125</option>
<option value="150" dorsal="175">GESINK Robert: 150</option>
<option value="100" dorsal="144">GIBBONS Ryan: 100</option>
<option value="75" dorsal="163">GONÇALVES José: 75</option>
<option value="75" dorsal="74">GROSSSCHARTNER Felix: 75</option>
<option value="100" dorsal="54">GUARDINI Andrea: 100</option>
<option value="50" dorsal="3">HAGA Chad: 50</option>
<option value="100" dorsal="113">HAIG Jack: 100</option>
<option value="50" dorsal="4">HAMILTON Chris: 50</option>
<option value="50" dorsal="107">HANSEN Adam: 50</option>
<option value="125" dorsal="184">HENAO Sergio Luis: 125</option>
<option value="125" dorsal="91">HERMANS Ben: 125</option>
<option value="100" dorsal="33">HIRT Jan: 100</option>
<option value="50" dorsal="5">HOFSTEDE Lennard: 50</option>
<option value="50" dorsal="194">IRIZAR Markel: 50</option>
<option value="75" dorsal="147">JANSE VAN RENSBURG Jacques: 75</option>
<option value="50" dorsal="16">JAUREGUI Quentin: 50</option>
<option value="50" dorsal="114">JUUL-JENSEN Christopher: 50</option>
<option value="125" dorsal="34">KANGERT Tanel: 125</option>
<option value="50" dorsal="145">KING Benjamin: 50</option>
<option value="75" dorsal="185">KIRYIENKA Vasil: 75</option>
<option value="50" dorsal="186">KNEES Christian: 50</option>
<option value="125" dorsal="75">KONRAD Patrick: 125</option>
<option value="125" dorsal="115">KREUZIGER Roman: 125</option>
<option value="50" dorsal="164">KUZNETSOV Viacheslav: 50</option>
<option value="50" dorsal="83">LADAGNOUS Matthieu: 50</option>
<option value="50" dorsal="204">LAENGEN Vegard Stake : 50</option>
<option value="50" dorsal="165">LAMMERTINK Maurits: 50</option>
<option value="50" dorsal="177">LINDEMAN Bert-Jan: 50</option>
<option value="375" dorsal="31">LOPEZ Miguel Angel: 375</option>
<option value="75" dorsal="35">LUTSENKO Alexey: 75</option>
<option value="50" dorsal="55">MAESTRI Mirco: 50</option>
<option value="50" dorsal="205">MARCATO Marco: 50</option>
<option value="125" dorsal="211">MARECZKO Jakub: 125</option>
<option value="125" dorsal="166">MARTIN Tony: 125</option>
<option value="75" dorsal="26">MASNADA Fausto: 75</option>
<option value="200" dorsal="141">MEINTJES Louis: 200</option>
<option value="200" dorsal="156">MODOLO Sacha: 200</option>
<option value="100" dorsal="44">MOHORIC Matej: 100</option>
<option value="75" dorsal="17">MONTAGUTI Matteo: 75</option>
<option value="50" dorsal="84">MORABITO Steve: 50</option>
<option value="50" dorsal="206">MORI Manuele: 50</option>
<option value="75" dorsal="134">MØRKØV Michael: 75</option>
<option value="75" dorsal="215">MOSCA Jacopo: 75</option>
<option value="75" dorsal="195">MULLEN Ryan: 75</option>
<option value="75" dorsal="94">NEILANDS Krists: 75</option>
<option value="50" dorsal="45">NIBALI Antonio: 50</option>
<option value="100" dorsal="116">NIEVE Mikel: 100</option>
<option value="50" dorsal="95">NIV Guy: 50</option>
<option value="50" dorsal="46">NOVAK Domen: 50</option>
<option value="100" dorsal="146">O'CONNOR Ben: 100</option>
<option value="150" dorsal="6">OOMEN Sam: 150</option>
<option value="125" dorsal="196">PANTANO Jarlinson: 125</option>
<option value="75" dorsal="197">PEDERSEN Mads: 75</option>
<option value="50" dorsal="125">PEDRERO Antonio: 50</option>
<option value="50" dorsal="76">PFINGSTEN Christoph: 50</option>
<option value="375" dorsal="81">PINOT Thibaut: 375</option>
<option value="75" dorsal="167">PLANCKAERT Baptiste: 75</option>
<option value="75" dorsal="96">PLAZA Rubén: 75</option>
<option value="200" dorsal="187">POELS Wout: 200</option>
<option value="125" dorsal="207">POLANC Jan: 125</option>
<option value="300" dorsal="41">POZZOVIVO Domenico: 300</option>
<option value="75" dorsal="85">PREIDLER Georg: 75</option>
<option value="50" dorsal="188">PUCCIO Salvatore: 50</option>
<option value="50" dorsal="126">QUINTANA Dayer: 50</option>
<option value="125" dorsal="86">REICHENBACH Sebasatien: 125</option>
<option value="125" dorsal="65">ROCHE Nicolas: 125</option>
<option value="125" dorsal="66">ROELANDTS Jurgen: 125</option>
<option value="50" dorsal="87">ROUX Anthony: 50</option>
<option value="50" dorsal="88">ROY Jeremy: 50</option>
<option value="50" dorsal="135">SABATINI Fabio: 50</option>
<option value="50" dorsal="98">SAGIV Guy: 50</option>
<option value="150" dorsal="36">SANCHEZ Luis Leon: 150</option>
<option value="100" dorsal="97">SBARAGLI Kristian: 100</option>
<option value="75" dorsal="136">SCHACHMANN Maximilian: 75</option>
<option value="50" dorsal="78">SCHILLINGER Andreas: 50</option>
<option value="50" dorsal="152">SCULLY Thomas: 50</option>
<option value="75" dorsal="77">SELIG Rüdiger: 75</option>
<option value="50" dorsal="137">SÉNÉCHAL Florian: 50</option>
<option value="50" dorsal="56">SENNI Manuel: 50</option>
<option value="75" dorsal="127">SEPÚLVEDA Eduardo: 75</option>
<option value="50" dorsal="57">SIMION Paolo: 50</option>
<option value="100" dorsal="47">SIUTSOU Kanstantsin: 100</option>
<option value="75" dorsal="138">STYBAR Zdenek : 75</option>
<option value="75" dorsal="7">TEN DAM Laurens: 75</option>
<option value="50" dorsal="58">TONELLI Alessandro: 50</option>
<option value="125" dorsal="27">TORRES Rodolfo Andres: 125</option>
<option value="50" dorsal="117">TUFT Svein: 50</option>
<option value="50" dorsal="216">TURRIN Alex: 50</option>
<option value="175" dorsal="208">ULISSI Diego: 175</option>
<option value="75" dorsal="128">VALLS Rafael: 75</option>
<option value="75" dorsal="157">VAN ASBROECK Tom: 75</option>
<option value="75" dorsal="108">VAN DER SANDE Tosh: 75</option>
<option value="75" dorsal="174">VAN EMDEN Jos: 75</option>
<option value="50" dorsal="176">VAN HOECKE Gijs: 50</option>
<option value="75" dorsal="198">VAN POPPEL Boy: 75</option>
<option value="150" dorsal="178">VAN POPPEL Danny: 150</option>
<option value="50" dorsal="28">VENDRAME Andrea: 50</option>
<option value="50" dorsal="148">VENTER Jaco: 50</option>
<option value="50" dorsal="67">VENTOSO Francisco : 50</option>
<option value="75" dorsal="18">VENTURINI Clément: 75</option>
<option value="75" dorsal="8">VERVAEKE Louis: 75</option>
<option value="75" dorsal="37">VILLELLA Davide: 75</option>
<option value="125" dorsal="48">VISCONTI Giovanni: 125</option>
<option value="300" dorsal="131">VIVIANI Elia: 300</option>
<option value="50" dorsal="68">VLIEGEN Loïc: 50</option>
<option value="150" dorsal="101">WELLENS Tim: 150</option>
<option value="175" dorsal="158">WOODS Michael: 175</option>
<option value="50" dorsal="168">WÜRTZ SCHMIDT Mads: 50</option>
<option value="275" dorsal="118">YATES Simon: 275</option>
<option value="50" dorsal="217">ZARDINI Edoardo: 50</option>
<option value="50" dorsal="38">ZEITS Andrey: 50</option>
<option value="50" dorsal="218">ZHUPA Eugert: 50</option>
</tr><tr>
<td class="labels">C5 :&#160</td>
<td><select id="rider5" onChange="getCredits(); sumPrices(); getRemaining(); printDorsal();">
<option value="0" selected="selected">Selecciona un corredor</option>
<option value="50" dorsal="52">ANDREETTA Simone: 50</option>
<option value="100" dorsal="142">ANTON Igor: 100</option>
<option value="75" dorsal="102">ARMÉE Sander: 75</option>
<option value="375" dorsal="201">ARU Fabio: 375</option>
<option value="125" dorsal="202">ATAPUMA John Darwin: 125</option>
<option value="50" dorsal="103">BAK Lars Ytting: 50</option>
<option value="75" dorsal="22">BALLERINI Davide: 75</option>
<option value="75" dorsal="53">BARBIN Enrico: 75</option>
<option value="100" dorsal="171">BATTAGLIN Enrico: 100</option>
<option value="50" dorsal="161">BELKOV Maxim: 50</option>
<option value="75" dorsal="23">BELLETTI Manuel: 75</option>
<option value="50" dorsal="72">BENEDETTI Cesare: 50</option>
<option value="175" dorsal="172">BENNETT George: 175</option>
<option value="200" dorsal="73">BENNETT Sam: 200</option>
<option value="75" dorsal="143">BERHANE Natnael: 75</option>
<option value="50" dorsal="212">BERTAZZO Liam: 50</option>
<option value="100" dorsal="121">BETANCUR Carlos: 100</option>
<option value="50" dorsal="112">BEWLEY Sam: 50</option>
<option value="50" dorsal="12">BIDARD François: 50</option>
<option value="100" dorsal="32">BILBAO Pello: 100</option>
<option value="50" dorsal="42">BOARO Manuele: 50</option>
<option value="50" dorsal="92">BOIVIN Guillaume: 50</option>
<option value="150" dorsal="43">BONIFAZIO Niccolo: 150</option>
<option value="50" dorsal="82">BONNET William: 50</option>
<option value="75" dorsal="173">BOUWMAN Koen: 75</option>
<option value="125" dorsal="191">BRAMBILLA Gianluca: 125</option>
<option value="50" dorsal="151">BROWN Nathan: 50</option>
<option value="75" dorsal="104">CAMPENAERTS Victor: 75</option>
<option value="50" dorsal="132">CAPECCHI Eros: 50</option>
<option value="100" dorsal="122">CARAPAZ Richard: 100</option>
<option value="75" dorsal="153">CARTHY Hugh: 75</option>
<option value="100" dorsal="24">CATTANEO Mattia: 100</option>
<option value="75" dorsal="133">CAVAGNA Rémi: 75</option>
<option value="325" dorsal="111">CHAVES Johan Esteban: 325</option>
<option value="75" dorsal="13">CHÉREL Mickaël: 75</option>
<option value="100" dorsal="51">CICCONE Giulio: 100</option>
<option value="50" dorsal="213">COLEDAN Marco: 50</option>
<option value="50" dorsal="203">CONTI Valerio: 50</option>
<option value="50" dorsal="2">CURVERS Roy: 50</option>
<option value="175" dorsal="182">DE LA CRUZ David: 175</option>
<option value="50" dorsal="123">DE LA PARTE Víctor: 50</option>
<option value="100" dorsal="62">DE MARCHI Alessandro: 100</option>
<option value="125" dorsal="105">DEBUSSCHERE Jens: 125</option>
<option value="50" dorsal="93">DEMPSTER Zakkari: 50</option>
<option value="175" dorsal="61">DENNIS Rohan: 175</option>
<option value="50" dorsal="14">DENZ Nico: 50</option>
<option value="50" dorsal="192">DIDIER Laurent: 50</option>
<option value="50" dorsal="154">DOCKER Mitchell: 50</option>
<option value="75" dorsal="155">DOMBROWSKI Joe: 75</option>
<option value="75" dorsal="162">DOWSETT Alex: 75</option>
<option value="100" dorsal="63">DRUCKER Jean-Pierre: 100</option>
<option value="475" dorsal="1">DUMOULIN Tom: 475</option>
<option value="75" dorsal="15">DUPONT Hubert: 75</option>
<option value="75" dorsal="193">EG Niklas: 75</option>
<option value="75" dorsal="183">ELISSONDE Kenny: 75</option>
<option value="75" dorsal="124">FERNÁNDEZ Rubén: 75</option>
<option value="50" dorsal="214">FONZI Giuseppe: 50</option>
<option value="175" dorsal="71">FORMOLO Davide: 175</option>
<option value="75" dorsal="64">FRANKINY Kilian: 75</option>
<option value="50" dorsal="25">FRAPPORTI Marco: 50</option>
<option value="50" dorsal="106">FRISON Frederik: 50</option>
<option value="600" dorsal="181">FROOME Christopher: 600</option>
<option value="100" dorsal="21">GAVAZZI Francesco: 100</option>
<option value="125" dorsal="11">GENIEZ Alexandre: 125</option>
<option value="150" dorsal="175">GESINK Robert: 150</option>
<option value="100" dorsal="144">GIBBONS Ryan: 100</option>
<option value="75" dorsal="163">GONÇALVES José: 75</option>
<option value="75" dorsal="74">GROSSSCHARTNER Felix: 75</option>
<option value="100" dorsal="54">GUARDINI Andrea: 100</option>
<option value="50" dorsal="3">HAGA Chad: 50</option>
<option value="100" dorsal="113">HAIG Jack: 100</option>
<option value="50" dorsal="4">HAMILTON Chris: 50</option>
<option value="50" dorsal="107">HANSEN Adam: 50</option>
<option value="125" dorsal="184">HENAO Sergio Luis: 125</option>
<option value="125" dorsal="91">HERMANS Ben: 125</option>
<option value="100" dorsal="33">HIRT Jan: 100</option>
<option value="50" dorsal="5">HOFSTEDE Lennard: 50</option>
<option value="50" dorsal="194">IRIZAR Markel: 50</option>
<option value="75" dorsal="147">JANSE VAN RENSBURG Jacques: 75</option>
<option value="50" dorsal="16">JAUREGUI Quentin: 50</option>
<option value="50" dorsal="114">JUUL-JENSEN Christopher: 50</option>
<option value="125" dorsal="34">KANGERT Tanel: 125</option>
<option value="50" dorsal="145">KING Benjamin: 50</option>
<option value="75" dorsal="185">KIRYIENKA Vasil: 75</option>
<option value="50" dorsal="186">KNEES Christian: 50</option>
<option value="125" dorsal="75">KONRAD Patrick: 125</option>
<option value="125" dorsal="115">KREUZIGER Roman: 125</option>
<option value="50" dorsal="164">KUZNETSOV Viacheslav: 50</option>
<option value="50" dorsal="83">LADAGNOUS Matthieu: 50</option>
<option value="50" dorsal="204">LAENGEN Vegard Stake : 50</option>
<option value="50" dorsal="165">LAMMERTINK Maurits: 50</option>
<option value="50" dorsal="177">LINDEMAN Bert-Jan: 50</option>
<option value="375" dorsal="31">LOPEZ Miguel Angel: 375</option>
<option value="75" dorsal="35">LUTSENKO Alexey: 75</option>
<option value="50" dorsal="55">MAESTRI Mirco: 50</option>
<option value="50" dorsal="205">MARCATO Marco: 50</option>
<option value="125" dorsal="211">MARECZKO Jakub: 125</option>
<option value="125" dorsal="166">MARTIN Tony: 125</option>
<option value="75" dorsal="26">MASNADA Fausto: 75</option>
<option value="200" dorsal="141">MEINTJES Louis: 200</option>
<option value="200" dorsal="156">MODOLO Sacha: 200</option>
<option value="100" dorsal="44">MOHORIC Matej: 100</option>
<option value="75" dorsal="17">MONTAGUTI Matteo: 75</option>
<option value="50" dorsal="84">MORABITO Steve: 50</option>
<option value="50" dorsal="206">MORI Manuele: 50</option>
<option value="75" dorsal="134">MØRKØV Michael: 75</option>
<option value="75" dorsal="215">MOSCA Jacopo: 75</option>
<option value="75" dorsal="195">MULLEN Ryan: 75</option>
<option value="75" dorsal="94">NEILANDS Krists: 75</option>
<option value="50" dorsal="45">NIBALI Antonio: 50</option>
<option value="100" dorsal="116">NIEVE Mikel: 100</option>
<option value="50" dorsal="95">NIV Guy: 50</option>
<option value="50" dorsal="46">NOVAK Domen: 50</option>
<option value="100" dorsal="146">O'CONNOR Ben: 100</option>
<option value="150" dorsal="6">OOMEN Sam: 150</option>
<option value="125" dorsal="196">PANTANO Jarlinson: 125</option>
<option value="75" dorsal="197">PEDERSEN Mads: 75</option>
<option value="50" dorsal="125">PEDRERO Antonio: 50</option>
<option value="50" dorsal="76">PFINGSTEN Christoph: 50</option>
<option value="375" dorsal="81">PINOT Thibaut: 375</option>
<option value="75" dorsal="167">PLANCKAERT Baptiste: 75</option>
<option value="75" dorsal="96">PLAZA Rubén: 75</option>
<option value="200" dorsal="187">POELS Wout: 200</option>
<option value="125" dorsal="207">POLANC Jan: 125</option>
<option value="300" dorsal="41">POZZOVIVO Domenico: 300</option>
<option value="75" dorsal="85">PREIDLER Georg: 75</option>
<option value="50" dorsal="188">PUCCIO Salvatore: 50</option>
<option value="50" dorsal="126">QUINTANA Dayer: 50</option>
<option value="125" dorsal="86">REICHENBACH Sebasatien: 125</option>
<option value="125" dorsal="65">ROCHE Nicolas: 125</option>
<option value="125" dorsal="66">ROELANDTS Jurgen: 125</option>
<option value="50" dorsal="87">ROUX Anthony: 50</option>
<option value="50" dorsal="88">ROY Jeremy: 50</option>
<option value="50" dorsal="135">SABATINI Fabio: 50</option>
<option value="50" dorsal="98">SAGIV Guy: 50</option>
<option value="150" dorsal="36">SANCHEZ Luis Leon: 150</option>
<option value="100" dorsal="97">SBARAGLI Kristian: 100</option>
<option value="75" dorsal="136">SCHACHMANN Maximilian: 75</option>
<option value="50" dorsal="78">SCHILLINGER Andreas: 50</option>
<option value="50" dorsal="152">SCULLY Thomas: 50</option>
<option value="75" dorsal="77">SELIG Rüdiger: 75</option>
<option value="50" dorsal="137">SÉNÉCHAL Florian: 50</option>
<option value="50" dorsal="56">SENNI Manuel: 50</option>
<option value="75" dorsal="127">SEPÚLVEDA Eduardo: 75</option>
<option value="50" dorsal="57">SIMION Paolo: 50</option>
<option value="100" dorsal="47">SIUTSOU Kanstantsin: 100</option>
<option value="75" dorsal="138">STYBAR Zdenek : 75</option>
<option value="75" dorsal="7">TEN DAM Laurens: 75</option>
<option value="50" dorsal="58">TONELLI Alessandro: 50</option>
<option value="125" dorsal="27">TORRES Rodolfo Andres: 125</option>
<option value="50" dorsal="117">TUFT Svein: 50</option>
<option value="50" dorsal="216">TURRIN Alex: 50</option>
<option value="175" dorsal="208">ULISSI Diego: 175</option>
<option value="75" dorsal="128">VALLS Rafael: 75</option>
<option value="75" dorsal="157">VAN ASBROECK Tom: 75</option>
<option value="75" dorsal="108">VAN DER SANDE Tosh: 75</option>
<option value="75" dorsal="174">VAN EMDEN Jos: 75</option>
<option value="50" dorsal="176">VAN HOECKE Gijs: 50</option>
<option value="75" dorsal="198">VAN POPPEL Boy: 75</option>
<option value="150" dorsal="178">VAN POPPEL Danny: 150</option>
<option value="50" dorsal="28">VENDRAME Andrea: 50</option>
<option value="50" dorsal="148">VENTER Jaco: 50</option>
<option value="50" dorsal="67">VENTOSO Francisco : 50</option>
<option value="75" dorsal="18">VENTURINI Clément: 75</option>
<option value="75" dorsal="8">VERVAEKE Louis: 75</option>
<option value="75" dorsal="37">VILLELLA Davide: 75</option>
<option value="125" dorsal="48">VISCONTI Giovanni: 125</option>
<option value="300" dorsal="131">VIVIANI Elia: 300</option>
<option value="50" dorsal="68">VLIEGEN Loïc: 50</option>
<option value="150" dorsal="101">WELLENS Tim: 150</option>
<option value="175" dorsal="158">WOODS Michael: 175</option>
<option value="50" dorsal="168">WÜRTZ SCHMIDT Mads: 50</option>
<option value="275" dorsal="118">YATES Simon: 275</option>
<option value="50" dorsal="217">ZARDINI Edoardo: 50</option>
<option value="50" dorsal="38">ZEITS Andrey: 50</option>
<option value="50" dorsal="218">ZHUPA Eugert: 50</option>
</tr><tr>
<td class="labels">C6 :&#160</td>
<td><select id="rider6" onChange="getCredits(); sumPrices(); getRemaining(); printDorsal();">
<option value="0" selected="selected">Selecciona un corredor</option>
<option value="50" dorsal="52">ANDREETTA Simone: 50</option>
<option value="100" dorsal="142">ANTON Igor: 100</option>
<option value="75" dorsal="102">ARMÉE Sander: 75</option>
<option value="375" dorsal="201">ARU Fabio: 375</option>
<option value="125" dorsal="202">ATAPUMA John Darwin: 125</option>
<option value="50" dorsal="103">BAK Lars Ytting: 50</option>
<option value="75" dorsal="22">BALLERINI Davide: 75</option>
<option value="75" dorsal="53">BARBIN Enrico: 75</option>
<option value="100" dorsal="171">BATTAGLIN Enrico: 100</option>
<option value="50" dorsal="161">BELKOV Maxim: 50</option>
<option value="75" dorsal="23">BELLETTI Manuel: 75</option>
<option value="50" dorsal="72">BENEDETTI Cesare: 50</option>
<option value="175" dorsal="172">BENNETT George: 175</option>
<option value="200" dorsal="73">BENNETT Sam: 200</option>
<option value="75" dorsal="143">BERHANE Natnael: 75</option>
<option value="50" dorsal="212">BERTAZZO Liam: 50</option>
<option value="100" dorsal="121">BETANCUR Carlos: 100</option>
<option value="50" dorsal="112">BEWLEY Sam: 50</option>
<option value="50" dorsal="12">BIDARD François: 50</option>
<option value="100" dorsal="32">BILBAO Pello: 100</option>
<option value="50" dorsal="42">BOARO Manuele: 50</option>
<option value="50" dorsal="92">BOIVIN Guillaume: 50</option>
<option value="150" dorsal="43">BONIFAZIO Niccolo: 150</option>
<option value="50" dorsal="82">BONNET William: 50</option>
<option value="75" dorsal="173">BOUWMAN Koen: 75</option>
<option value="125" dorsal="191">BRAMBILLA Gianluca: 125</option>
<option value="50" dorsal="151">BROWN Nathan: 50</option>
<option value="75" dorsal="104">CAMPENAERTS Victor: 75</option>
<option value="50" dorsal="132">CAPECCHI Eros: 50</option>
<option value="100" dorsal="122">CARAPAZ Richard: 100</option>
<option value="75" dorsal="153">CARTHY Hugh: 75</option>
<option value="100" dorsal="24">CATTANEO Mattia: 100</option>
<option value="75" dorsal="133">CAVAGNA Rémi: 75</option>
<option value="325" dorsal="111">CHAVES Johan Esteban: 325</option>
<option value="75" dorsal="13">CHÉREL Mickaël: 75</option>
<option value="100" dorsal="51">CICCONE Giulio: 100</option>
<option value="50" dorsal="213">COLEDAN Marco: 50</option>
<option value="50" dorsal="203">CONTI Valerio: 50</option>
<option value="50" dorsal="2">CURVERS Roy: 50</option>
<option value="175" dorsal="182">DE LA CRUZ David: 175</option>
<option value="50" dorsal="123">DE LA PARTE Víctor: 50</option>
<option value="100" dorsal="62">DE MARCHI Alessandro: 100</option>
<option value="125" dorsal="105">DEBUSSCHERE Jens: 125</option>
<option value="50" dorsal="93">DEMPSTER Zakkari: 50</option>
<option value="175" dorsal="61">DENNIS Rohan: 175</option>
<option value="50" dorsal="14">DENZ Nico: 50</option>
<option value="50" dorsal="192">DIDIER Laurent: 50</option>
<option value="50" dorsal="154">DOCKER Mitchell: 50</option>
<option value="75" dorsal="155">DOMBROWSKI Joe: 75</option>
<option value="75" dorsal="162">DOWSETT Alex: 75</option>
<option value="100" dorsal="63">DRUCKER Jean-Pierre: 100</option>
<option value="475" dorsal="1">DUMOULIN Tom: 475</option>
<option value="75" dorsal="15">DUPONT Hubert: 75</option>
<option value="75" dorsal="193">EG Niklas: 75</option>
<option value="75" dorsal="183">ELISSONDE Kenny: 75</option>
<option value="75" dorsal="124">FERNÁNDEZ Rubén: 75</option>
<option value="50" dorsal="214">FONZI Giuseppe: 50</option>
<option value="175" dorsal="71">FORMOLO Davide: 175</option>
<option value="75" dorsal="64">FRANKINY Kilian: 75</option>
<option value="50" dorsal="25">FRAPPORTI Marco: 50</option>
<option value="50" dorsal="106">FRISON Frederik: 50</option>
<option value="600" dorsal="181">FROOME Christopher: 600</option>
<option value="100" dorsal="21">GAVAZZI Francesco: 100</option>
<option value="125" dorsal="11">GENIEZ Alexandre: 125</option>
<option value="150" dorsal="175">GESINK Robert: 150</option>
<option value="100" dorsal="144">GIBBONS Ryan: 100</option>
<option value="75" dorsal="163">GONÇALVES José: 75</option>
<option value="75" dorsal="74">GROSSSCHARTNER Felix: 75</option>
<option value="100" dorsal="54">GUARDINI Andrea: 100</option>
<option value="50" dorsal="3">HAGA Chad: 50</option>
<option value="100" dorsal="113">HAIG Jack: 100</option>
<option value="50" dorsal="4">HAMILTON Chris: 50</option>
<option value="50" dorsal="107">HANSEN Adam: 50</option>
<option value="125" dorsal="184">HENAO Sergio Luis: 125</option>
<option value="125" dorsal="91">HERMANS Ben: 125</option>
<option value="100" dorsal="33">HIRT Jan: 100</option>
<option value="50" dorsal="5">HOFSTEDE Lennard: 50</option>
<option value="50" dorsal="194">IRIZAR Markel: 50</option>
<option value="75" dorsal="147">JANSE VAN RENSBURG Jacques: 75</option>
<option value="50" dorsal="16">JAUREGUI Quentin: 50</option>
<option value="50" dorsal="114">JUUL-JENSEN Christopher: 50</option>
<option value="125" dorsal="34">KANGERT Tanel: 125</option>
<option value="50" dorsal="145">KING Benjamin: 50</option>
<option value="75" dorsal="185">KIRYIENKA Vasil: 75</option>
<option value="50" dorsal="186">KNEES Christian: 50</option>
<option value="125" dorsal="75">KONRAD Patrick: 125</option>
<option value="125" dorsal="115">KREUZIGER Roman: 125</option>
<option value="50" dorsal="164">KUZNETSOV Viacheslav: 50</option>
<option value="50" dorsal="83">LADAGNOUS Matthieu: 50</option>
<option value="50" dorsal="204">LAENGEN Vegard Stake : 50</option>
<option value="50" dorsal="165">LAMMERTINK Maurits: 50</option>
<option value="50" dorsal="177">LINDEMAN Bert-Jan: 50</option>
<option value="375" dorsal="31">LOPEZ Miguel Angel: 375</option>
<option value="75" dorsal="35">LUTSENKO Alexey: 75</option>
<option value="50" dorsal="55">MAESTRI Mirco: 50</option>
<option value="50" dorsal="205">MARCATO Marco: 50</option>
<option value="125" dorsal="211">MARECZKO Jakub: 125</option>
<option value="125" dorsal="166">MARTIN Tony: 125</option>
<option value="75" dorsal="26">MASNADA Fausto: 75</option>
<option value="200" dorsal="141">MEINTJES Louis: 200</option>
<option value="200" dorsal="156">MODOLO Sacha: 200</option>
<option value="100" dorsal="44">MOHORIC Matej: 100</option>
<option value="75" dorsal="17">MONTAGUTI Matteo: 75</option>
<option value="50" dorsal="84">MORABITO Steve: 50</option>
<option value="50" dorsal="206">MORI Manuele: 50</option>
<option value="75" dorsal="134">MØRKØV Michael: 75</option>
<option value="75" dorsal="215">MOSCA Jacopo: 75</option>
<option value="75" dorsal="195">MULLEN Ryan: 75</option>
<option value="75" dorsal="94">NEILANDS Krists: 75</option>
<option value="50" dorsal="45">NIBALI Antonio: 50</option>
<option value="100" dorsal="116">NIEVE Mikel: 100</option>
<option value="50" dorsal="95">NIV Guy: 50</option>
<option value="50" dorsal="46">NOVAK Domen: 50</option>
<option value="100" dorsal="146">O'CONNOR Ben: 100</option>
<option value="150" dorsal="6">OOMEN Sam: 150</option>
<option value="125" dorsal="196">PANTANO Jarlinson: 125</option>
<option value="75" dorsal="197">PEDERSEN Mads: 75</option>
<option value="50" dorsal="125">PEDRERO Antonio: 50</option>
<option value="50" dorsal="76">PFINGSTEN Christoph: 50</option>
<option value="375" dorsal="81">PINOT Thibaut: 375</option>
<option value="75" dorsal="167">PLANCKAERT Baptiste: 75</option>
<option value="75" dorsal="96">PLAZA Rubén: 75</option>
<option value="200" dorsal="187">POELS Wout: 200</option>
<option value="125" dorsal="207">POLANC Jan: 125</option>
<option value="300" dorsal="41">POZZOVIVO Domenico: 300</option>
<option value="75" dorsal="85">PREIDLER Georg: 75</option>
<option value="50" dorsal="188">PUCCIO Salvatore: 50</option>
<option value="50" dorsal="126">QUINTANA Dayer: 50</option>
<option value="125" dorsal="86">REICHENBACH Sebasatien: 125</option>
<option value="125" dorsal="65">ROCHE Nicolas: 125</option>
<option value="125" dorsal="66">ROELANDTS Jurgen: 125</option>
<option value="50" dorsal="87">ROUX Anthony: 50</option>
<option value="50" dorsal="88">ROY Jeremy: 50</option>
<option value="50" dorsal="135">SABATINI Fabio: 50</option>
<option value="50" dorsal="98">SAGIV Guy: 50</option>
<option value="150" dorsal="36">SANCHEZ Luis Leon: 150</option>
<option value="100" dorsal="97">SBARAGLI Kristian: 100</option>
<option value="75" dorsal="136">SCHACHMANN Maximilian: 75</option>
<option value="50" dorsal="78">SCHILLINGER Andreas: 50</option>
<option value="50" dorsal="152">SCULLY Thomas: 50</option>
<option value="75" dorsal="77">SELIG Rüdiger: 75</option>
<option value="50" dorsal="137">SÉNÉCHAL Florian: 50</option>
<option value="50" dorsal="56">SENNI Manuel: 50</option>
<option value="75" dorsal="127">SEPÚLVEDA Eduardo: 75</option>
<option value="50" dorsal="57">SIMION Paolo: 50</option>
<option value="100" dorsal="47">SIUTSOU Kanstantsin: 100</option>
<option value="75" dorsal="138">STYBAR Zdenek : 75</option>
<option value="75" dorsal="7">TEN DAM Laurens: 75</option>
<option value="50" dorsal="58">TONELLI Alessandro: 50</option>
<option value="125" dorsal="27">TORRES Rodolfo Andres: 125</option>
<option value="50" dorsal="117">TUFT Svein: 50</option>
<option value="50" dorsal="216">TURRIN Alex: 50</option>
<option value="175" dorsal="208">ULISSI Diego: 175</option>
<option value="75" dorsal="128">VALLS Rafael: 75</option>
<option value="75" dorsal="157">VAN ASBROECK Tom: 75</option>
<option value="75" dorsal="108">VAN DER SANDE Tosh: 75</option>
<option value="75" dorsal="174">VAN EMDEN Jos: 75</option>
<option value="50" dorsal="176">VAN HOECKE Gijs: 50</option>
<option value="75" dorsal="198">VAN POPPEL Boy: 75</option>
<option value="150" dorsal="178">VAN POPPEL Danny: 150</option>
<option value="50" dorsal="28">VENDRAME Andrea: 50</option>
<option value="50" dorsal="148">VENTER Jaco: 50</option>
<option value="50" dorsal="67">VENTOSO Francisco : 50</option>
<option value="75" dorsal="18">VENTURINI Clément: 75</option>
<option value="75" dorsal="8">VERVAEKE Louis: 75</option>
<option value="75" dorsal="37">VILLELLA Davide: 75</option>
<option value="125" dorsal="48">VISCONTI Giovanni: 125</option>
<option value="300" dorsal="131">VIVIANI Elia: 300</option>
<option value="50" dorsal="68">VLIEGEN Loïc: 50</option>
<option value="150" dorsal="101">WELLENS Tim: 150</option>
<option value="175" dorsal="158">WOODS Michael: 175</option>
<option value="50" dorsal="168">WÜRTZ SCHMIDT Mads: 50</option>
<option value="275" dorsal="118">YATES Simon: 275</option>
<option value="50" dorsal="217">ZARDINI Edoardo: 50</option>
<option value="50" dorsal="38">ZEITS Andrey: 50</option>
<option value="50" dorsal="218">ZHUPA Eugert: 50</option>
</tr><tr>
<td class="labels">C7 :&#160</td>
<td><select id="rider7" onChange="getCredits(); sumPrices(); getRemaining(); printDorsal();">
<option value="0" selected="selected">Selecciona un corredor</option>
<option value="50" dorsal="52">ANDREETTA Simone: 50</option>
<option value="100" dorsal="142">ANTON Igor: 100</option>
<option value="75" dorsal="102">ARMÉE Sander: 75</option>
<option value="375" dorsal="201">ARU Fabio: 375</option>
<option value="125" dorsal="202">ATAPUMA John Darwin: 125</option>
<option value="50" dorsal="103">BAK Lars Ytting: 50</option>
<option value="75" dorsal="22">BALLERINI Davide: 75</option>
<option value="75" dorsal="53">BARBIN Enrico: 75</option>
<option value="100" dorsal="171">BATTAGLIN Enrico: 100</option>
<option value="50" dorsal="161">BELKOV Maxim: 50</option>
<option value="75" dorsal="23">BELLETTI Manuel: 75</option>
<option value="50" dorsal="72">BENEDETTI Cesare: 50</option>
<option value="175" dorsal="172">BENNETT George: 175</option>
<option value="200" dorsal="73">BENNETT Sam: 200</option>
<option value="75" dorsal="143">BERHANE Natnael: 75</option>
<option value="50" dorsal="212">BERTAZZO Liam: 50</option>
<option value="100" dorsal="121">BETANCUR Carlos: 100</option>
<option value="50" dorsal="112">BEWLEY Sam: 50</option>
<option value="50" dorsal="12">BIDARD François: 50</option>
<option value="100" dorsal="32">BILBAO Pello: 100</option>
<option value="50" dorsal="42">BOARO Manuele: 50</option>
<option value="50" dorsal="92">BOIVIN Guillaume: 50</option>
<option value="150" dorsal="43">BONIFAZIO Niccolo: 150</option>
<option value="50" dorsal="82">BONNET William: 50</option>
<option value="75" dorsal="173">BOUWMAN Koen: 75</option>
<option value="125" dorsal="191">BRAMBILLA Gianluca: 125</option>
<option value="50" dorsal="151">BROWN Nathan: 50</option>
<option value="75" dorsal="104">CAMPENAERTS Victor: 75</option>
<option value="50" dorsal="132">CAPECCHI Eros: 50</option>
<option value="100" dorsal="122">CARAPAZ Richard: 100</option>
<option value="75" dorsal="153">CARTHY Hugh: 75</option>
<option value="100" dorsal="24">CATTANEO Mattia: 100</option>
<option value="75" dorsal="133">CAVAGNA Rémi: 75</option>
<option value="325" dorsal="111">CHAVES Johan Esteban: 325</option>
<option value="75" dorsal="13">CHÉREL Mickaël: 75</option>
<option value="100" dorsal="51">CICCONE Giulio: 100</option>
<option value="50" dorsal="213">COLEDAN Marco: 50</option>
<option value="50" dorsal="203">CONTI Valerio: 50</option>
<option value="50" dorsal="2">CURVERS Roy: 50</option>
<option value="175" dorsal="182">DE LA CRUZ David: 175</option>
<option value="50" dorsal="123">DE LA PARTE Víctor: 50</option>
<option value="100" dorsal="62">DE MARCHI Alessandro: 100</option>
<option value="125" dorsal="105">DEBUSSCHERE Jens: 125</option>
<option value="50" dorsal="93">DEMPSTER Zakkari: 50</option>
<option value="175" dorsal="61">DENNIS Rohan: 175</option>
<option value="50" dorsal="14">DENZ Nico: 50</option>
<option value="50" dorsal="192">DIDIER Laurent: 50</option>
<option value="50" dorsal="154">DOCKER Mitchell: 50</option>
<option value="75" dorsal="155">DOMBROWSKI Joe: 75</option>
<option value="75" dorsal="162">DOWSETT Alex: 75</option>
<option value="100" dorsal="63">DRUCKER Jean-Pierre: 100</option>
<option value="475" dorsal="1">DUMOULIN Tom: 475</option>
<option value="75" dorsal="15">DUPONT Hubert: 75</option>
<option value="75" dorsal="193">EG Niklas: 75</option>
<option value="75" dorsal="183">ELISSONDE Kenny: 75</option>
<option value="75" dorsal="124">FERNÁNDEZ Rubén: 75</option>
<option value="50" dorsal="214">FONZI Giuseppe: 50</option>
<option value="175" dorsal="71">FORMOLO Davide: 175</option>
<option value="75" dorsal="64">FRANKINY Kilian: 75</option>
<option value="50" dorsal="25">FRAPPORTI Marco: 50</option>
<option value="50" dorsal="106">FRISON Frederik: 50</option>
<option value="600" dorsal="181">FROOME Christopher: 600</option>
<option value="100" dorsal="21">GAVAZZI Francesco: 100</option>
<option value="125" dorsal="11">GENIEZ Alexandre: 125</option>
<option value="150" dorsal="175">GESINK Robert: 150</option>
<option value="100" dorsal="144">GIBBONS Ryan: 100</option>
<option value="75" dorsal="163">GONÇALVES José: 75</option>
<option value="75" dorsal="74">GROSSSCHARTNER Felix: 75</option>
<option value="100" dorsal="54">GUARDINI Andrea: 100</option>
<option value="50" dorsal="3">HAGA Chad: 50</option>
<option value="100" dorsal="113">HAIG Jack: 100</option>
<option value="50" dorsal="4">HAMILTON Chris: 50</option>
<option value="50" dorsal="107">HANSEN Adam: 50</option>
<option value="125" dorsal="184">HENAO Sergio Luis: 125</option>
<option value="125" dorsal="91">HERMANS Ben: 125</option>
<option value="100" dorsal="33">HIRT Jan: 100</option>
<option value="50" dorsal="5">HOFSTEDE Lennard: 50</option>
<option value="50" dorsal="194">IRIZAR Markel: 50</option>
<option value="75" dorsal="147">JANSE VAN RENSBURG Jacques: 75</option>
<option value="50" dorsal="16">JAUREGUI Quentin: 50</option>
<option value="50" dorsal="114">JUUL-JENSEN Christopher: 50</option>
<option value="125" dorsal="34">KANGERT Tanel: 125</option>
<option value="50" dorsal="145">KING Benjamin: 50</option>
<option value="75" dorsal="185">KIRYIENKA Vasil: 75</option>
<option value="50" dorsal="186">KNEES Christian: 50</option>
<option value="125" dorsal="75">KONRAD Patrick: 125</option>
<option value="125" dorsal="115">KREUZIGER Roman: 125</option>
<option value="50" dorsal="164">KUZNETSOV Viacheslav: 50</option>
<option value="50" dorsal="83">LADAGNOUS Matthieu: 50</option>
<option value="50" dorsal="204">LAENGEN Vegard Stake : 50</option>
<option value="50" dorsal="165">LAMMERTINK Maurits: 50</option>
<option value="50" dorsal="177">LINDEMAN Bert-Jan: 50</option>
<option value="375" dorsal="31">LOPEZ Miguel Angel: 375</option>
<option value="75" dorsal="35">LUTSENKO Alexey: 75</option>
<option value="50" dorsal="55">MAESTRI Mirco: 50</option>
<option value="50" dorsal="205">MARCATO Marco: 50</option>
<option value="125" dorsal="211">MARECZKO Jakub: 125</option>
<option value="125" dorsal="166">MARTIN Tony: 125</option>
<option value="75" dorsal="26">MASNADA Fausto: 75</option>
<option value="200" dorsal="141">MEINTJES Louis: 200</option>
<option value="200" dorsal="156">MODOLO Sacha: 200</option>
<option value="100" dorsal="44">MOHORIC Matej: 100</option>
<option value="75" dorsal="17">MONTAGUTI Matteo: 75</option>
<option value="50" dorsal="84">MORABITO Steve: 50</option>
<option value="50" dorsal="206">MORI Manuele: 50</option>
<option value="75" dorsal="134">MØRKØV Michael: 75</option>
<option value="75" dorsal="215">MOSCA Jacopo: 75</option>
<option value="75" dorsal="195">MULLEN Ryan: 75</option>
<option value="75" dorsal="94">NEILANDS Krists: 75</option>
<option value="50" dorsal="45">NIBALI Antonio: 50</option>
<option value="100" dorsal="116">NIEVE Mikel: 100</option>
<option value="50" dorsal="95">NIV Guy: 50</option>
<option value="50" dorsal="46">NOVAK Domen: 50</option>
<option value="100" dorsal="146">O'CONNOR Ben: 100</option>
<option value="150" dorsal="6">OOMEN Sam: 150</option>
<option value="125" dorsal="196">PANTANO Jarlinson: 125</option>
<option value="75" dorsal="197">PEDERSEN Mads: 75</option>
<option value="50" dorsal="125">PEDRERO Antonio: 50</option>
<option value="50" dorsal="76">PFINGSTEN Christoph: 50</option>
<option value="375" dorsal="81">PINOT Thibaut: 375</option>
<option value="75" dorsal="167">PLANCKAERT Baptiste: 75</option>
<option value="75" dorsal="96">PLAZA Rubén: 75</option>
<option value="200" dorsal="187">POELS Wout: 200</option>
<option value="125" dorsal="207">POLANC Jan: 125</option>
<option value="300" dorsal="41">POZZOVIVO Domenico: 300</option>
<option value="75" dorsal="85">PREIDLER Georg: 75</option>
<option value="50" dorsal="188">PUCCIO Salvatore: 50</option>
<option value="50" dorsal="126">QUINTANA Dayer: 50</option>
<option value="125" dorsal="86">REICHENBACH Sebasatien: 125</option>
<option value="125" dorsal="65">ROCHE Nicolas: 125</option>
<option value="125" dorsal="66">ROELANDTS Jurgen: 125</option>
<option value="50" dorsal="87">ROUX Anthony: 50</option>
<option value="50" dorsal="88">ROY Jeremy: 50</option>
<option value="50" dorsal="135">SABATINI Fabio: 50</option>
<option value="50" dorsal="98">SAGIV Guy: 50</option>
<option value="150" dorsal="36">SANCHEZ Luis Leon: 150</option>
<option value="100" dorsal="97">SBARAGLI Kristian: 100</option>
<option value="75" dorsal="136">SCHACHMANN Maximilian: 75</option>
<option value="50" dorsal="78">SCHILLINGER Andreas: 50</option>
<option value="50" dorsal="152">SCULLY Thomas: 50</option>
<option value="75" dorsal="77">SELIG Rüdiger: 75</option>
<option value="50" dorsal="137">SÉNÉCHAL Florian: 50</option>
<option value="50" dorsal="56">SENNI Manuel: 50</option>
<option value="75" dorsal="127">SEPÚLVEDA Eduardo: 75</option>
<option value="50" dorsal="57">SIMION Paolo: 50</option>
<option value="100" dorsal="47">SIUTSOU Kanstantsin: 100</option>
<option value="75" dorsal="138">STYBAR Zdenek : 75</option>
<option value="75" dorsal="7">TEN DAM Laurens: 75</option>
<option value="50" dorsal="58">TONELLI Alessandro: 50</option>
<option value="125" dorsal="27">TORRES Rodolfo Andres: 125</option>
<option value="50" dorsal="117">TUFT Svein: 50</option>
<option value="50" dorsal="216">TURRIN Alex: 50</option>
<option value="175" dorsal="208">ULISSI Diego: 175</option>
<option value="75" dorsal="128">VALLS Rafael: 75</option>
<option value="75" dorsal="157">VAN ASBROECK Tom: 75</option>
<option value="75" dorsal="108">VAN DER SANDE Tosh: 75</option>
<option value="75" dorsal="174">VAN EMDEN Jos: 75</option>
<option value="50" dorsal="176">VAN HOECKE Gijs: 50</option>
<option value="75" dorsal="198">VAN POPPEL Boy: 75</option>
<option value="150" dorsal="178">VAN POPPEL Danny: 150</option>
<option value="50" dorsal="28">VENDRAME Andrea: 50</option>
<option value="50" dorsal="148">VENTER Jaco: 50</option>
<option value="50" dorsal="67">VENTOSO Francisco : 50</option>
<option value="75" dorsal="18">VENTURINI Clément: 75</option>
<option value="75" dorsal="8">VERVAEKE Louis: 75</option>
<option value="75" dorsal="37">VILLELLA Davide: 75</option>
<option value="125" dorsal="48">VISCONTI Giovanni: 125</option>
<option value="300" dorsal="131">VIVIANI Elia: 300</option>
<option value="50" dorsal="68">VLIEGEN Loïc: 50</option>
<option value="150" dorsal="101">WELLENS Tim: 150</option>
<option value="175" dorsal="158">WOODS Michael: 175</option>
<option value="50" dorsal="168">WÜRTZ SCHMIDT Mads: 50</option>
<option value="275" dorsal="118">YATES Simon: 275</option>
<option value="50" dorsal="217">ZARDINI Edoardo: 50</option>
<option value="50" dorsal="38">ZEITS Andrey: 50</option>
<option value="50" dorsal="218">ZHUPA Eugert: 50</option>
</tr><tr>
<td class="labels">C8 :&#160</td>
<td><select id="rider8" onChange="getCredits(); sumPrices(); getRemaining(); printDorsal();">
<option value="0" selected="selected">Selecciona un corredor</option>
<option value="50" dorsal="52">ANDREETTA Simone: 50</option>
<option value="100" dorsal="142">ANTON Igor: 100</option>
<option value="75" dorsal="102">ARMÉE Sander: 75</option>
<option value="375" dorsal="201">ARU Fabio: 375</option>
<option value="125" dorsal="202">ATAPUMA John Darwin: 125</option>
<option value="50" dorsal="103">BAK Lars Ytting: 50</option>
<option value="75" dorsal="22">BALLERINI Davide: 75</option>
<option value="75" dorsal="53">BARBIN Enrico: 75</option>
<option value="100" dorsal="171">BATTAGLIN Enrico: 100</option>
<option value="50" dorsal="161">BELKOV Maxim: 50</option>
<option value="75" dorsal="23">BELLETTI Manuel: 75</option>
<option value="50" dorsal="72">BENEDETTI Cesare: 50</option>
<option value="175" dorsal="172">BENNETT George: 175</option>
<option value="200" dorsal="73">BENNETT Sam: 200</option>
<option value="75" dorsal="143">BERHANE Natnael: 75</option>
<option value="50" dorsal="212">BERTAZZO Liam: 50</option>
<option value="100" dorsal="121">BETANCUR Carlos: 100</option>
<option value="50" dorsal="112">BEWLEY Sam: 50</option>
<option value="50" dorsal="12">BIDARD François: 50</option>
<option value="100" dorsal="32">BILBAO Pello: 100</option>
<option value="50" dorsal="42">BOARO Manuele: 50</option>
<option value="50" dorsal="92">BOIVIN Guillaume: 50</option>
<option value="150" dorsal="43">BONIFAZIO Niccolo: 150</option>
<option value="50" dorsal="82">BONNET William: 50</option>
<option value="75" dorsal="173">BOUWMAN Koen: 75</option>
<option value="125" dorsal="191">BRAMBILLA Gianluca: 125</option>
<option value="50" dorsal="151">BROWN Nathan: 50</option>
<option value="75" dorsal="104">CAMPENAERTS Victor: 75</option>
<option value="50" dorsal="132">CAPECCHI Eros: 50</option>
<option value="100" dorsal="122">CARAPAZ Richard: 100</option>
<option value="75" dorsal="153">CARTHY Hugh: 75</option>
<option value="100" dorsal="24">CATTANEO Mattia: 100</option>
<option value="75" dorsal="133">CAVAGNA Rémi: 75</option>
<option value="325" dorsal="111">CHAVES Johan Esteban: 325</option>
<option value="75" dorsal="13">CHÉREL Mickaël: 75</option>
<option value="100" dorsal="51">CICCONE Giulio: 100</option>
<option value="50" dorsal="213">COLEDAN Marco: 50</option>
<option value="50" dorsal="203">CONTI Valerio: 50</option>
<option value="50" dorsal="2">CURVERS Roy: 50</option>
<option value="175" dorsal="182">DE LA CRUZ David: 175</option>
<option value="50" dorsal="123">DE LA PARTE Víctor: 50</option>
<option value="100" dorsal="62">DE MARCHI Alessandro: 100</option>
<option value="125" dorsal="105">DEBUSSCHERE Jens: 125</option>
<option value="50" dorsal="93">DEMPSTER Zakkari: 50</option>
<option value="175" dorsal="61">DENNIS Rohan: 175</option>
<option value="50" dorsal="14">DENZ Nico: 50</option>
<option value="50" dorsal="192">DIDIER Laurent: 50</option>
<option value="50" dorsal="154">DOCKER Mitchell: 50</option>
<option value="75" dorsal="155">DOMBROWSKI Joe: 75</option>
<option value="75" dorsal="162">DOWSETT Alex: 75</option>
<option value="100" dorsal="63">DRUCKER Jean-Pierre: 100</option>
<option value="475" dorsal="1">DUMOULIN Tom: 475</option>
<option value="75" dorsal="15">DUPONT Hubert: 75</option>
<option value="75" dorsal="193">EG Niklas: 75</option>
<option value="75" dorsal="183">ELISSONDE Kenny: 75</option>
<option value="75" dorsal="124">FERNÁNDEZ Rubén: 75</option>
<option value="50" dorsal="214">FONZI Giuseppe: 50</option>
<option value="175" dorsal="71">FORMOLO Davide: 175</option>
<option value="75" dorsal="64">FRANKINY Kilian: 75</option>
<option value="50" dorsal="25">FRAPPORTI Marco: 50</option>
<option value="50" dorsal="106">FRISON Frederik: 50</option>
<option value="600" dorsal="181">FROOME Christopher: 600</option>
<option value="100" dorsal="21">GAVAZZI Francesco: 100</option>
<option value="125" dorsal="11">GENIEZ Alexandre: 125</option>
<option value="150" dorsal="175">GESINK Robert: 150</option>
<option value="100" dorsal="144">GIBBONS Ryan: 100</option>
<option value="75" dorsal="163">GONÇALVES José: 75</option>
<option value="75" dorsal="74">GROSSSCHARTNER Felix: 75</option>
<option value="100" dorsal="54">GUARDINI Andrea: 100</option>
<option value="50" dorsal="3">HAGA Chad: 50</option>
<option value="100" dorsal="113">HAIG Jack: 100</option>
<option value="50" dorsal="4">HAMILTON Chris: 50</option>
<option value="50" dorsal="107">HANSEN Adam: 50</option>
<option value="125" dorsal="184">HENAO Sergio Luis: 125</option>
<option value="125" dorsal="91">HERMANS Ben: 125</option>
<option value="100" dorsal="33">HIRT Jan: 100</option>
<option value="50" dorsal="5">HOFSTEDE Lennard: 50</option>
<option value="50" dorsal="194">IRIZAR Markel: 50</option>
<option value="75" dorsal="147">JANSE VAN RENSBURG Jacques: 75</option>
<option value="50" dorsal="16">JAUREGUI Quentin: 50</option>
<option value="50" dorsal="114">JUUL-JENSEN Christopher: 50</option>
<option value="125" dorsal="34">KANGERT Tanel: 125</option>
<option value="50" dorsal="145">KING Benjamin: 50</option>
<option value="75" dorsal="185">KIRYIENKA Vasil: 75</option>
<option value="50" dorsal="186">KNEES Christian: 50</option>
<option value="125" dorsal="75">KONRAD Patrick: 125</option>
<option value="125" dorsal="115">KREUZIGER Roman: 125</option>
<option value="50" dorsal="164">KUZNETSOV Viacheslav: 50</option>
<option value="50" dorsal="83">LADAGNOUS Matthieu: 50</option>
<option value="50" dorsal="204">LAENGEN Vegard Stake : 50</option>
<option value="50" dorsal="165">LAMMERTINK Maurits: 50</option>
<option value="50" dorsal="177">LINDEMAN Bert-Jan: 50</option>
<option value="375" dorsal="31">LOPEZ Miguel Angel: 375</option>
<option value="75" dorsal="35">LUTSENKO Alexey: 75</option>
<option value="50" dorsal="55">MAESTRI Mirco: 50</option>
<option value="50" dorsal="205">MARCATO Marco: 50</option>
<option value="125" dorsal="211">MARECZKO Jakub: 125</option>
<option value="125" dorsal="166">MARTIN Tony: 125</option>
<option value="75" dorsal="26">MASNADA Fausto: 75</option>
<option value="200" dorsal="141">MEINTJES Louis: 200</option>
<option value="200" dorsal="156">MODOLO Sacha: 200</option>
<option value="100" dorsal="44">MOHORIC Matej: 100</option>
<option value="75" dorsal="17">MONTAGUTI Matteo: 75</option>
<option value="50" dorsal="84">MORABITO Steve: 50</option>
<option value="50" dorsal="206">MORI Manuele: 50</option>
<option value="75" dorsal="134">MØRKØV Michael: 75</option>
<option value="75" dorsal="215">MOSCA Jacopo: 75</option>
<option value="75" dorsal="195">MULLEN Ryan: 75</option>
<option value="75" dorsal="94">NEILANDS Krists: 75</option>
<option value="50" dorsal="45">NIBALI Antonio: 50</option>
<option value="100" dorsal="116">NIEVE Mikel: 100</option>
<option value="50" dorsal="95">NIV Guy: 50</option>
<option value="50" dorsal="46">NOVAK Domen: 50</option>
<option value="100" dorsal="146">O'CONNOR Ben: 100</option>
<option value="150" dorsal="6">OOMEN Sam: 150</option>
<option value="125" dorsal="196">PANTANO Jarlinson: 125</option>
<option value="75" dorsal="197">PEDERSEN Mads: 75</option>
<option value="50" dorsal="125">PEDRERO Antonio: 50</option>
<option value="50" dorsal="76">PFINGSTEN Christoph: 50</option>
<option value="375" dorsal="81">PINOT Thibaut: 375</option>
<option value="75" dorsal="167">PLANCKAERT Baptiste: 75</option>
<option value="75" dorsal="96">PLAZA Rubén: 75</option>
<option value="200" dorsal="187">POELS Wout: 200</option>
<option value="125" dorsal="207">POLANC Jan: 125</option>
<option value="300" dorsal="41">POZZOVIVO Domenico: 300</option>
<option value="75" dorsal="85">PREIDLER Georg: 75</option>
<option value="50" dorsal="188">PUCCIO Salvatore: 50</option>
<option value="50" dorsal="126">QUINTANA Dayer: 50</option>
<option value="125" dorsal="86">REICHENBACH Sebasatien: 125</option>
<option value="125" dorsal="65">ROCHE Nicolas: 125</option>
<option value="125" dorsal="66">ROELANDTS Jurgen: 125</option>
<option value="50" dorsal="87">ROUX Anthony: 50</option>
<option value="50" dorsal="88">ROY Jeremy: 50</option>
<option value="50" dorsal="135">SABATINI Fabio: 50</option>
<option value="50" dorsal="98">SAGIV Guy: 50</option>
<option value="150" dorsal="36">SANCHEZ Luis Leon: 150</option>
<option value="100" dorsal="97">SBARAGLI Kristian: 100</option>
<option value="75" dorsal="136">SCHACHMANN Maximilian: 75</option>
<option value="50" dorsal="78">SCHILLINGER Andreas: 50</option>
<option value="50" dorsal="152">SCULLY Thomas: 50</option>
<option value="75" dorsal="77">SELIG Rüdiger: 75</option>
<option value="50" dorsal="137">SÉNÉCHAL Florian: 50</option>
<option value="50" dorsal="56">SENNI Manuel: 50</option>
<option value="75" dorsal="127">SEPÚLVEDA Eduardo: 75</option>
<option value="50" dorsal="57">SIMION Paolo: 50</option>
<option value="100" dorsal="47">SIUTSOU Kanstantsin: 100</option>
<option value="75" dorsal="138">STYBAR Zdenek : 75</option>
<option value="75" dorsal="7">TEN DAM Laurens: 75</option>
<option value="50" dorsal="58">TONELLI Alessandro: 50</option>
<option value="125" dorsal="27">TORRES Rodolfo Andres: 125</option>
<option value="50" dorsal="117">TUFT Svein: 50</option>
<option value="50" dorsal="216">TURRIN Alex: 50</option>
<option value="175" dorsal="208">ULISSI Diego: 175</option>
<option value="75" dorsal="128">VALLS Rafael: 75</option>
<option value="75" dorsal="157">VAN ASBROECK Tom: 75</option>
<option value="75" dorsal="108">VAN DER SANDE Tosh: 75</option>
<option value="75" dorsal="174">VAN EMDEN Jos: 75</option>
<option value="50" dorsal="176">VAN HOECKE Gijs: 50</option>
<option value="75" dorsal="198">VAN POPPEL Boy: 75</option>
<option value="150" dorsal="178">VAN POPPEL Danny: 150</option>
<option value="50" dorsal="28">VENDRAME Andrea: 50</option>
<option value="50" dorsal="148">VENTER Jaco: 50</option>
<option value="50" dorsal="67">VENTOSO Francisco : 50</option>
<option value="75" dorsal="18">VENTURINI Clément: 75</option>
<option value="75" dorsal="8">VERVAEKE Louis: 75</option>
<option value="75" dorsal="37">VILLELLA Davide: 75</option>
<option value="125" dorsal="48">VISCONTI Giovanni: 125</option>
<option value="300" dorsal="131">VIVIANI Elia: 300</option>
<option value="50" dorsal="68">VLIEGEN Loïc: 50</option>
<option value="150" dorsal="101">WELLENS Tim: 150</option>
<option value="175" dorsal="158">WOODS Michael: 175</option>
<option value="50" dorsal="168">WÜRTZ SCHMIDT Mads: 50</option>
<option value="275" dorsal="118">YATES Simon: 275</option>
<option value="50" dorsal="217">ZARDINI Edoardo: 50</option>
<option value="50" dorsal="38">ZEITS Andrey: 50</option>
<option value="50" dorsal="218">ZHUPA Eugert: 50</option>
</tr><tr>
<td class="labels">C9 :&#160</td>
<td><select id="rider9" onChange="getCredits(); sumPrices(); getRemaining(); printDorsal();">
<option value="0" selected="selected">Selecciona un corredor</option>
<option value="50" dorsal="52">ANDREETTA Simone: 50</option>
<option value="100" dorsal="142">ANTON Igor: 100</option>
<option value="75" dorsal="102">ARMÉE Sander: 75</option>
<option value="375" dorsal="201">ARU Fabio: 375</option>
<option value="125" dorsal="202">ATAPUMA John Darwin: 125</option>
<option value="50" dorsal="103">BAK Lars Ytting: 50</option>
<option value="75" dorsal="22">BALLERINI Davide: 75</option>
<option value="75" dorsal="53">BARBIN Enrico: 75</option>
<option value="100" dorsal="171">BATTAGLIN Enrico: 100</option>
<option value="50" dorsal="161">BELKOV Maxim: 50</option>
<option value="75" dorsal="23">BELLETTI Manuel: 75</option>
<option value="50" dorsal="72">BENEDETTI Cesare: 50</option>
<option value="175" dorsal="172">BENNETT George: 175</option>
<option value="200" dorsal="73">BENNETT Sam: 200</option>
<option value="75" dorsal="143">BERHANE Natnael: 75</option>
<option value="50" dorsal="212">BERTAZZO Liam: 50</option>
<option value="100" dorsal="121">BETANCUR Carlos: 100</option>
<option value="50" dorsal="112">BEWLEY Sam: 50</option>
<option value="50" dorsal="12">BIDARD François: 50</option>
<option value="100" dorsal="32">BILBAO Pello: 100</option>
<option value="50" dorsal="42">BOARO Manuele: 50</option>
<option value="50" dorsal="92">BOIVIN Guillaume: 50</option>
<option value="150" dorsal="43">BONIFAZIO Niccolo: 150</option>
<option value="50" dorsal="82">BONNET William: 50</option>
<option value="75" dorsal="173">BOUWMAN Koen: 75</option>
<option value="125" dorsal="191">BRAMBILLA Gianluca: 125</option>
<option value="50" dorsal="151">BROWN Nathan: 50</option>
<option value="75" dorsal="104">CAMPENAERTS Victor: 75</option>
<option value="50" dorsal="132">CAPECCHI Eros: 50</option>
<option value="100" dorsal="122">CARAPAZ Richard: 100</option>
<option value="75" dorsal="153">CARTHY Hugh: 75</option>
<option value="100" dorsal="24">CATTANEO Mattia: 100</option>
<option value="75" dorsal="133">CAVAGNA Rémi: 75</option>
<option value="325" dorsal="111">CHAVES Johan Esteban: 325</option>
<option value="75" dorsal="13">CHÉREL Mickaël: 75</option>
<option value="100" dorsal="51">CICCONE Giulio: 100</option>
<option value="50" dorsal="213">COLEDAN Marco: 50</option>
<option value="50" dorsal="203">CONTI Valerio: 50</option>
<option value="50" dorsal="2">CURVERS Roy: 50</option>
<option value="175" dorsal="182">DE LA CRUZ David: 175</option>
<option value="50" dorsal="123">DE LA PARTE Víctor: 50</option>
<option value="100" dorsal="62">DE MARCHI Alessandro: 100</option>
<option value="125" dorsal="105">DEBUSSCHERE Jens: 125</option>
<option value="50" dorsal="93">DEMPSTER Zakkari: 50</option>
<option value="175" dorsal="61">DENNIS Rohan: 175</option>
<option value="50" dorsal="14">DENZ Nico: 50</option>
<option value="50" dorsal="192">DIDIER Laurent: 50</option>
<option value="50" dorsal="154">DOCKER Mitchell: 50</option>
<option value="75" dorsal="155">DOMBROWSKI Joe: 75</option>
<option value="75" dorsal="162">DOWSETT Alex: 75</option>
<option value="100" dorsal="63">DRUCKER Jean-Pierre: 100</option>
<option value="475" dorsal="1">DUMOULIN Tom: 475</option>
<option value="75" dorsal="15">DUPONT Hubert: 75</option>
<option value="75" dorsal="193">EG Niklas: 75</option>
<option value="75" dorsal="183">ELISSONDE Kenny: 75</option>
<option value="75" dorsal="124">FERNÁNDEZ Rubén: 75</option>
<option value="50" dorsal="214">FONZI Giuseppe: 50</option>
<option value="175" dorsal="71">FORMOLO Davide: 175</option>
<option value="75" dorsal="64">FRANKINY Kilian: 75</option>
<option value="50" dorsal="25">FRAPPORTI Marco: 50</option>
<option value="50" dorsal="106">FRISON Frederik: 50</option>
<option value="600" dorsal="181">FROOME Christopher: 600</option>
<option value="100" dorsal="21">GAVAZZI Francesco: 100</option>
<option value="125" dorsal="11">GENIEZ Alexandre: 125</option>
<option value="150" dorsal="175">GESINK Robert: 150</option>
<option value="100" dorsal="144">GIBBONS Ryan: 100</option>
<option value="75" dorsal="163">GONÇALVES José: 75</option>
<option value="75" dorsal="74">GROSSSCHARTNER Felix: 75</option>
<option value="100" dorsal="54">GUARDINI Andrea: 100</option>
<option value="50" dorsal="3">HAGA Chad: 50</option>
<option value="100" dorsal="113">HAIG Jack: 100</option>
<option value="50" dorsal="4">HAMILTON Chris: 50</option>
<option value="50" dorsal="107">HANSEN Adam: 50</option>
<option value="125" dorsal="184">HENAO Sergio Luis: 125</option>
<option value="125" dorsal="91">HERMANS Ben: 125</option>
<option value="100" dorsal="33">HIRT Jan: 100</option>
<option value="50" dorsal="5">HOFSTEDE Lennard: 50</option>
<option value="50" dorsal="194">IRIZAR Markel: 50</option>
<option value="75" dorsal="147">JANSE VAN RENSBURG Jacques: 75</option>
<option value="50" dorsal="16">JAUREGUI Quentin: 50</option>
<option value="50" dorsal="114">JUUL-JENSEN Christopher: 50</option>
<option value="125" dorsal="34">KANGERT Tanel: 125</option>
<option value="50" dorsal="145">KING Benjamin: 50</option>
<option value="75" dorsal="185">KIRYIENKA Vasil: 75</option>
<option value="50" dorsal="186">KNEES Christian: 50</option>
<option value="125" dorsal="75">KONRAD Patrick: 125</option>
<option value="125" dorsal="115">KREUZIGER Roman: 125</option>
<option value="50" dorsal="164">KUZNETSOV Viacheslav: 50</option>
<option value="50" dorsal="83">LADAGNOUS Matthieu: 50</option>
<option value="50" dorsal="204">LAENGEN Vegard Stake : 50</option>
<option value="50" dorsal="165">LAMMERTINK Maurits: 50</option>
<option value="50" dorsal="177">LINDEMAN Bert-Jan: 50</option>
<option value="375" dorsal="31">LOPEZ Miguel Angel: 375</option>
<option value="75" dorsal="35">LUTSENKO Alexey: 75</option>
<option value="50" dorsal="55">MAESTRI Mirco: 50</option>
<option value="50" dorsal="205">MARCATO Marco: 50</option>
<option value="125" dorsal="211">MARECZKO Jakub: 125</option>
<option value="125" dorsal="166">MARTIN Tony: 125</option>
<option value="75" dorsal="26">MASNADA Fausto: 75</option>
<option value="200" dorsal="141">MEINTJES Louis: 200</option>
<option value="200" dorsal="156">MODOLO Sacha: 200</option>
<option value="100" dorsal="44">MOHORIC Matej: 100</option>
<option value="75" dorsal="17">MONTAGUTI Matteo: 75</option>
<option value="50" dorsal="84">MORABITO Steve: 50</option>
<option value="50" dorsal="206">MORI Manuele: 50</option>
<option value="75" dorsal="134">MØRKØV Michael: 75</option>
<option value="75" dorsal="215">MOSCA Jacopo: 75</option>
<option value="75" dorsal="195">MULLEN Ryan: 75</option>
<option value="75" dorsal="94">NEILANDS Krists: 75</option>
<option value="50" dorsal="45">NIBALI Antonio: 50</option>
<option value="100" dorsal="116">NIEVE Mikel: 100</option>
<option value="50" dorsal="95">NIV Guy: 50</option>
<option value="50" dorsal="46">NOVAK Domen: 50</option>
<option value="100" dorsal="146">O'CONNOR Ben: 100</option>
<option value="150" dorsal="6">OOMEN Sam: 150</option>
<option value="125" dorsal="196">PANTANO Jarlinson: 125</option>
<option value="75" dorsal="197">PEDERSEN Mads: 75</option>
<option value="50" dorsal="125">PEDRERO Antonio: 50</option>
<option value="50" dorsal="76">PFINGSTEN Christoph: 50</option>
<option value="375" dorsal="81">PINOT Thibaut: 375</option>
<option value="75" dorsal="167">PLANCKAERT Baptiste: 75</option>
<option value="75" dorsal="96">PLAZA Rubén: 75</option>
<option value="200" dorsal="187">POELS Wout: 200</option>
<option value="125" dorsal="207">POLANC Jan: 125</option>
<option value="300" dorsal="41">POZZOVIVO Domenico: 300</option>
<option value="75" dorsal="85">PREIDLER Georg: 75</option>
<option value="50" dorsal="188">PUCCIO Salvatore: 50</option>
<option value="50" dorsal="126">QUINTANA Dayer: 50</option>
<option value="125" dorsal="86">REICHENBACH Sebasatien: 125</option>
<option value="125" dorsal="65">ROCHE Nicolas: 125</option>
<option value="125" dorsal="66">ROELANDTS Jurgen: 125</option>
<option value="50" dorsal="87">ROUX Anthony: 50</option>
<option value="50" dorsal="88">ROY Jeremy: 50</option>
<option value="50" dorsal="135">SABATINI Fabio: 50</option>
<option value="50" dorsal="98">SAGIV Guy: 50</option>
<option value="150" dorsal="36">SANCHEZ Luis Leon: 150</option>
<option value="100" dorsal="97">SBARAGLI Kristian: 100</option>
<option value="75" dorsal="136">SCHACHMANN Maximilian: 75</option>
<option value="50" dorsal="78">SCHILLINGER Andreas: 50</option>
<option value="50" dorsal="152">SCULLY Thomas: 50</option>
<option value="75" dorsal="77">SELIG Rüdiger: 75</option>
<option value="50" dorsal="137">SÉNÉCHAL Florian: 50</option>
<option value="50" dorsal="56">SENNI Manuel: 50</option>
<option value="75" dorsal="127">SEPÚLVEDA Eduardo: 75</option>
<option value="50" dorsal="57">SIMION Paolo: 50</option>
<option value="100" dorsal="47">SIUTSOU Kanstantsin: 100</option>
<option value="75" dorsal="138">STYBAR Zdenek : 75</option>
<option value="75" dorsal="7">TEN DAM Laurens: 75</option>
<option value="50" dorsal="58">TONELLI Alessandro: 50</option>
<option value="125" dorsal="27">TORRES Rodolfo Andres: 125</option>
<option value="50" dorsal="117">TUFT Svein: 50</option>
<option value="50" dorsal="216">TURRIN Alex: 50</option>
<option value="175" dorsal="208">ULISSI Diego: 175</option>
<option value="75" dorsal="128">VALLS Rafael: 75</option>
<option value="75" dorsal="157">VAN ASBROECK Tom: 75</option>
<option value="75" dorsal="108">VAN DER SANDE Tosh: 75</option>
<option value="75" dorsal="174">VAN EMDEN Jos: 75</option>
<option value="50" dorsal="176">VAN HOECKE Gijs: 50</option>
<option value="75" dorsal="198">VAN POPPEL Boy: 75</option>
<option value="150" dorsal="178">VAN POPPEL Danny: 150</option>
<option value="50" dorsal="28">VENDRAME Andrea: 50</option>
<option value="50" dorsal="148">VENTER Jaco: 50</option>
<option value="50" dorsal="67">VENTOSO Francisco : 50</option>
<option value="75" dorsal="18">VENTURINI Clément: 75</option>
<option value="75" dorsal="8">VERVAEKE Louis: 75</option>
<option value="75" dorsal="37">VILLELLA Davide: 75</option>
<option value="125" dorsal="48">VISCONTI Giovanni: 125</option>
<option value="300" dorsal="131">VIVIANI Elia: 300</option>
<option value="50" dorsal="68">VLIEGEN Loïc: 50</option>
<option value="150" dorsal="101">WELLENS Tim: 150</option>
<option value="175" dorsal="158">WOODS Michael: 175</option>
<option value="50" dorsal="168">WÜRTZ SCHMIDT Mads: 50</option>
<option value="275" dorsal="118">YATES Simon: 275</option>
<option value="50" dorsal="217">ZARDINI Edoardo: 50</option>
<option value="50" dorsal="38">ZEITS Andrey: 50</option>
<option value="50" dorsal="218">ZHUPA Eugert: 50</option>
</tr><tr>
<td class="labels">R :&#160</td>
<td><select id="reserve" onChange="getCredits(); sumPrices(); getRemaining(); printDorsal();">
<option value="0" selected="selected">Selecciona un corredor</option>
<option value="50" dorsal="52">ANDREETTA Simone: 50</option>
<option value="100" dorsal="142">ANTON Igor: 100</option>
<option value="75" dorsal="102">ARMÉE Sander: 75</option>
<option value="375" dorsal="201">ARU Fabio: 375</option>
<option value="125" dorsal="202">ATAPUMA John Darwin: 125</option>
<option value="50" dorsal="103">BAK Lars Ytting: 50</option>
<option value="75" dorsal="22">BALLERINI Davide: 75</option>
<option value="75" dorsal="53">BARBIN Enrico: 75</option>
<option value="100" dorsal="171">BATTAGLIN Enrico: 100</option>
<option value="50" dorsal="161">BELKOV Maxim: 50</option>
<option value="75" dorsal="23">BELLETTI Manuel: 75</option>
<option value="50" dorsal="72">BENEDETTI Cesare: 50</option>
<option value="175" dorsal="172">BENNETT George: 175</option>
<option value="200" dorsal="73">BENNETT Sam: 200</option>
<option value="75" dorsal="143">BERHANE Natnael: 75</option>
<option value="50" dorsal="212">BERTAZZO Liam: 50</option>
<option value="100" dorsal="121">BETANCUR Carlos: 100</option>
<option value="50" dorsal="112">BEWLEY Sam: 50</option>
<option value="50" dorsal="12">BIDARD François: 50</option>
<option value="100" dorsal="32">BILBAO Pello: 100</option>
<option value="50" dorsal="42">BOARO Manuele: 50</option>
<option value="50" dorsal="92">BOIVIN Guillaume: 50</option>
<option value="150" dorsal="43">BONIFAZIO Niccolo: 150</option>
<option value="50" dorsal="82">BONNET William: 50</option>
<option value="75" dorsal="173">BOUWMAN Koen: 75</option>
<option value="125" dorsal="191">BRAMBILLA Gianluca: 125</option>
<option value="50" dorsal="151">BROWN Nathan: 50</option>
<option value="75" dorsal="104">CAMPENAERTS Victor: 75</option>
<option value="50" dorsal="132">CAPECCHI Eros: 50</option>
<option value="100" dorsal="122">CARAPAZ Richard: 100</option>
<option value="75" dorsal="153">CARTHY Hugh: 75</option>
<option value="100" dorsal="24">CATTANEO Mattia: 100</option>
<option value="75" dorsal="133">CAVAGNA Rémi: 75</option>
<option value="325" dorsal="111">CHAVES Johan Esteban: 325</option>
<option value="75" dorsal="13">CHÉREL Mickaël: 75</option>
<option value="100" dorsal="51">CICCONE Giulio: 100</option>
<option value="50" dorsal="213">COLEDAN Marco: 50</option>
<option value="50" dorsal="203">CONTI Valerio: 50</option>
<option value="50" dorsal="2">CURVERS Roy: 50</option>
<option value="175" dorsal="182">DE LA CRUZ David: 175</option>
<option value="50" dorsal="123">DE LA PARTE Víctor: 50</option>
<option value="100" dorsal="62">DE MARCHI Alessandro: 100</option>
<option value="125" dorsal="105">DEBUSSCHERE Jens: 125</option>
<option value="50" dorsal="93">DEMPSTER Zakkari: 50</option>
<option value="175" dorsal="61">DENNIS Rohan: 175</option>
<option value="50" dorsal="14">DENZ Nico: 50</option>
<option value="50" dorsal="192">DIDIER Laurent: 50</option>
<option value="50" dorsal="154">DOCKER Mitchell: 50</option>
<option value="75" dorsal="155">DOMBROWSKI Joe: 75</option>
<option value="75" dorsal="162">DOWSETT Alex: 75</option>
<option value="100" dorsal="63">DRUCKER Jean-Pierre: 100</option>
<option value="475" dorsal="1">DUMOULIN Tom: 475</option>
<option value="75" dorsal="15">DUPONT Hubert: 75</option>
<option value="75" dorsal="193">EG Niklas: 75</option>
<option value="75" dorsal="183">ELISSONDE Kenny: 75</option>
<option value="75" dorsal="124">FERNÁNDEZ Rubén: 75</option>
<option value="50" dorsal="214">FONZI Giuseppe: 50</option>
<option value="175" dorsal="71">FORMOLO Davide: 175</option>
<option value="75" dorsal="64">FRANKINY Kilian: 75</option>
<option value="50" dorsal="25">FRAPPORTI Marco: 50</option>
<option value="50" dorsal="106">FRISON Frederik: 50</option>
<option value="600" dorsal="181">FROOME Christopher: 600</option>
<option value="100" dorsal="21">GAVAZZI Francesco: 100</option>
<option value="125" dorsal="11">GENIEZ Alexandre: 125</option>
<option value="150" dorsal="175">GESINK Robert: 150</option>
<option value="100" dorsal="144">GIBBONS Ryan: 100</option>
<option value="75" dorsal="163">GONÇALVES José: 75</option>
<option value="75" dorsal="74">GROSSSCHARTNER Felix: 75</option>
<option value="100" dorsal="54">GUARDINI Andrea: 100</option>
<option value="50" dorsal="3">HAGA Chad: 50</option>
<option value="100" dorsal="113">HAIG Jack: 100</option>
<option value="50" dorsal="4">HAMILTON Chris: 50</option>
<option value="50" dorsal="107">HANSEN Adam: 50</option>
<option value="125" dorsal="184">HENAO Sergio Luis: 125</option>
<option value="125" dorsal="91">HERMANS Ben: 125</option>
<option value="100" dorsal="33">HIRT Jan: 100</option>
<option value="50" dorsal="5">HOFSTEDE Lennard: 50</option>
<option value="50" dorsal="194">IRIZAR Markel: 50</option>
<option value="75" dorsal="147">JANSE VAN RENSBURG Jacques: 75</option>
<option value="50" dorsal="16">JAUREGUI Quentin: 50</option>
<option value="50" dorsal="114">JUUL-JENSEN Christopher: 50</option>
<option value="125" dorsal="34">KANGERT Tanel: 125</option>
<option value="50" dorsal="145">KING Benjamin: 50</option>
<option value="75" dorsal="185">KIRYIENKA Vasil: 75</option>
<option value="50" dorsal="186">KNEES Christian: 50</option>
<option value="125" dorsal="75">KONRAD Patrick: 125</option>
<option value="125" dorsal="115">KREUZIGER Roman: 125</option>
<option value="50" dorsal="164">KUZNETSOV Viacheslav: 50</option>
<option value="50" dorsal="83">LADAGNOUS Matthieu: 50</option>
<option value="50" dorsal="204">LAENGEN Vegard Stake : 50</option>
<option value="50" dorsal="165">LAMMERTINK Maurits: 50</option>
<option value="50" dorsal="177">LINDEMAN Bert-Jan: 50</option>
<option value="375" dorsal="31">LOPEZ Miguel Angel: 375</option>
<option value="75" dorsal="35">LUTSENKO Alexey: 75</option>
<option value="50" dorsal="55">MAESTRI Mirco: 50</option>
<option value="50" dorsal="205">MARCATO Marco: 50</option>
<option value="125" dorsal="211">MARECZKO Jakub: 125</option>
<option value="125" dorsal="166">MARTIN Tony: 125</option>
<option value="75" dorsal="26">MASNADA Fausto: 75</option>
<option value="200" dorsal="141">MEINTJES Louis: 200</option>
<option value="200" dorsal="156">MODOLO Sacha: 200</option>
<option value="100" dorsal="44">MOHORIC Matej: 100</option>
<option value="75" dorsal="17">MONTAGUTI Matteo: 75</option>
<option value="50" dorsal="84">MORABITO Steve: 50</option>
<option value="50" dorsal="206">MORI Manuele: 50</option>
<option value="75" dorsal="134">MØRKØV Michael: 75</option>
<option value="75" dorsal="215">MOSCA Jacopo: 75</option>
<option value="75" dorsal="195">MULLEN Ryan: 75</option>
<option value="75" dorsal="94">NEILANDS Krists: 75</option>
<option value="50" dorsal="45">NIBALI Antonio: 50</option>
<option value="100" dorsal="116">NIEVE Mikel: 100</option>
<option value="50" dorsal="95">NIV Guy: 50</option>
<option value="50" dorsal="46">NOVAK Domen: 50</option>
<option value="100" dorsal="146">O'CONNOR Ben: 100</option>
<option value="150" dorsal="6">OOMEN Sam: 150</option>
<option value="125" dorsal="196">PANTANO Jarlinson: 125</option>
<option value="75" dorsal="197">PEDERSEN Mads: 75</option>
<option value="50" dorsal="125">PEDRERO Antonio: 50</option>
<option value="50" dorsal="76">PFINGSTEN Christoph: 50</option>
<option value="375" dorsal="81">PINOT Thibaut: 375</option>
<option value="75" dorsal="167">PLANCKAERT Baptiste: 75</option>
<option value="75" dorsal="96">PLAZA Rubén: 75</option>
<option value="200" dorsal="187">POELS Wout: 200</option>
<option value="125" dorsal="207">POLANC Jan: 125</option>
<option value="300" dorsal="41">POZZOVIVO Domenico: 300</option>
<option value="75" dorsal="85">PREIDLER Georg: 75</option>
<option value="50" dorsal="188">PUCCIO Salvatore: 50</option>
<option value="50" dorsal="126">QUINTANA Dayer: 50</option>
<option value="125" dorsal="86">REICHENBACH Sebasatien: 125</option>
<option value="125" dorsal="65">ROCHE Nicolas: 125</option>
<option value="125" dorsal="66">ROELANDTS Jurgen: 125</option>
<option value="50" dorsal="87">ROUX Anthony: 50</option>
<option value="50" dorsal="88">ROY Jeremy: 50</option>
<option value="50" dorsal="135">SABATINI Fabio: 50</option>
<option value="50" dorsal="98">SAGIV Guy: 50</option>
<option value="150" dorsal="36">SANCHEZ Luis Leon: 150</option>
<option value="100" dorsal="97">SBARAGLI Kristian: 100</option>
<option value="75" dorsal="136">SCHACHMANN Maximilian: 75</option>
<option value="50" dorsal="78">SCHILLINGER Andreas: 50</option>
<option value="50" dorsal="152">SCULLY Thomas: 50</option>
<option value="75" dorsal="77">SELIG Rüdiger: 75</option>
<option value="50" dorsal="137">SÉNÉCHAL Florian: 50</option>
<option value="50" dorsal="56">SENNI Manuel: 50</option>
<option value="75" dorsal="127">SEPÚLVEDA Eduardo: 75</option>
<option value="50" dorsal="57">SIMION Paolo: 50</option>
<option value="100" dorsal="47">SIUTSOU Kanstantsin: 100</option>
<option value="75" dorsal="138">STYBAR Zdenek : 75</option>
<option value="75" dorsal="7">TEN DAM Laurens: 75</option>
<option value="50" dorsal="58">TONELLI Alessandro: 50</option>
<option value="125" dorsal="27">TORRES Rodolfo Andres: 125</option>
<option value="50" dorsal="117">TUFT Svein: 50</option>
<option value="50" dorsal="216">TURRIN Alex: 50</option>
<option value="175" dorsal="208">ULISSI Diego: 175</option>
<option value="75" dorsal="128">VALLS Rafael: 75</option>
<option value="75" dorsal="157">VAN ASBROECK Tom: 75</option>
<option value="75" dorsal="108">VAN DER SANDE Tosh: 75</option>
<option value="75" dorsal="174">VAN EMDEN Jos: 75</option>
<option value="50" dorsal="176">VAN HOECKE Gijs: 50</option>
<option value="75" dorsal="198">VAN POPPEL Boy: 75</option>
<option value="150" dorsal="178">VAN POPPEL Danny: 150</option>
<option value="50" dorsal="28">VENDRAME Andrea: 50</option>
<option value="50" dorsal="148">VENTER Jaco: 50</option>
<option value="50" dorsal="67">VENTOSO Francisco : 50</option>
<option value="75" dorsal="18">VENTURINI Clément: 75</option>
<option value="75" dorsal="8">VERVAEKE Louis: 75</option>
<option value="75" dorsal="37">VILLELLA Davide: 75</option>
<option value="125" dorsal="48">VISCONTI Giovanni: 125</option>
<option value="300" dorsal="131">VIVIANI Elia: 300</option>
<option value="50" dorsal="68">VLIEGEN Loïc: 50</option>
<option value="150" dorsal="101">WELLENS Tim: 150</option>
<option value="175" dorsal="158">WOODS Michael: 175</option>
<option value="50" dorsal="168">WÜRTZ SCHMIDT Mads: 50</option>
<option value="275" dorsal="118">YATES Simon: 275</option>
<option value="50" dorsal="217">ZARDINI Edoardo: 50</option>
<option value="50" dorsal="38">ZEITS Andrey: 50</option>
<option value="50" dorsal="218">ZHUPA Eugert: 50</option>
</tr></table>
<br>
<p>Listado de dorsales:</p>
<textarea id="dorsalList" rows="11">

</textarea> 
<br>

<button class="submitButtons" onclick="sendMail()">Enviar por mail</button>
<button class="submitButtons" id="copyList">Copiar lista</button>
<br>
<br>
<p class="info">* Enviar por mail: Rellena tu nombre de usuario en el Foro y selecciona los 9 corredores (reserva opcional). Tras ello, haz clic en el botón en tu móvil o PC con cliente de correo predefinido (si tienes) y rellenará automáticamente el mail que debes mandar. Revisa la selección y envía el correo.
<br>
<br>
* Copiar lista: Copiará tu selección al portapapeles.</p>
<br>


<script>
	$("button" + "#copyList").click(function(){
    $("textarea").select();
    document.execCommand('copy');
});

	getCredits();
	sumPrices();
	getRemaining();

	var totalPrice = 0;
	var credits = 0;
	var remaining = 0;
	var repeated = false;

	var budgetError = "Atención: Te has pasado de presupuesto."
	var repeatedError = "Atención: Ciclistas repetidos.";
	var userError = "Introduce tu usuario del foro ACB.";
	var divError = "Selecciona una división.";

	var state = 0;
	document.getElementById('profiles').style.display = "none";

	var state2 = 0;
	document.getElementById('ridersByPriceTR').style.display = "none";

	function getCredits()
	{
		credits = document.getElementById('divisions').value;
		document.getElementById('budget').innerHTML = credits;
	}

	function getRemaining() 
	{
		remaining = credits - totalPrice;
		document.getElementById('remainingBudget').innerHTML = remaining;

		if(remaining < 0)
		{

			document.getElementById('error').innerHTML = budgetError;

		}
		else
		{
			if(document.getElementById('error').innerHTML == budgetError)
			{
				document.getElementById('error').innerHTML = "";
			}
		}
	}

	function sumPrices(){
			
	totalPrice = 0;
	arrayDorsal = [];
	arrayCyclists = [];

		var price1 = parseInt(document.getElementById('rider1').value);
		var price2 = parseInt(document.getElementById('rider2').value);
		var price3 = parseInt(document.getElementById('rider3').value);
		var price4 = parseInt(document.getElementById('rider4').value);
		var price5 = parseInt(document.getElementById('rider5').value);
		var price6 = parseInt(document.getElementById('rider6').value);
		var price7 = parseInt(document.getElementById('rider7').value);
		var price8 = parseInt(document.getElementById('rider8').value);
		var price9 = parseInt(document.getElementById('rider9').value);

		totalPrice +=  price1 + price2 + price3 + price4 + price5 + price6 + price7 + price8 + price9; 

		var rider1Dorsal = document.getElementById('rider1').options[document.getElementById('rider1').selectedIndex].getAttribute('dorsal');
		var rider2Dorsal = document.getElementById('rider2').options[document.getElementById('rider2').selectedIndex].getAttribute('dorsal');
		var rider3Dorsal = document.getElementById('rider3').options[document.getElementById('rider3').selectedIndex].getAttribute('dorsal');
		var rider4Dorsal = document.getElementById('rider4').options[document.getElementById('rider4').selectedIndex].getAttribute('dorsal');
		var rider5Dorsal = document.getElementById('rider5').options[document.getElementById('rider5').selectedIndex].getAttribute('dorsal');
		var rider6Dorsal = document.getElementById('rider6').options[document.getElementById('rider6').selectedIndex].getAttribute('dorsal');
		var rider7Dorsal = document.getElementById('rider7').options[document.getElementById('rider7').selectedIndex].getAttribute('dorsal');
		var rider8Dorsal = document.getElementById('rider8').options[document.getElementById('rider8').selectedIndex].getAttribute('dorsal');
		var rider9Dorsal = document.getElementById('rider9').options[document.getElementById('rider9').selectedIndex].getAttribute('dorsal');
		var reserveDorsal = document.getElementById('reserve').options[document.getElementById('reserve').selectedIndex].getAttribute('dorsal');

		var rider1Name = document.getElementById('rider1').options[document.getElementById('rider1').selectedIndex].text;
		var rider2Name = document.getElementById('rider2').options[document.getElementById('rider2').selectedIndex].text;
		var rider3Name = document.getElementById('rider3').options[document.getElementById('rider3').selectedIndex].text;
		var rider4Name = document.getElementById('rider4').options[document.getElementById('rider4').selectedIndex].text;
		var rider5Name = document.getElementById('rider5').options[document.getElementById('rider5').selectedIndex].text;
		var rider6Name = document.getElementById('rider6').options[document.getElementById('rider6').selectedIndex].text;
		var rider7Name = document.getElementById('rider7').options[document.getElementById('rider7').selectedIndex].text;
		var rider8Name = document.getElementById('rider8').options[document.getElementById('rider8').selectedIndex].text;
		var rider9Name = document.getElementById('rider9').options[document.getElementById('rider9').selectedIndex].text;
		var reserveName = document.getElementById('reserve').options[document.getElementById('reserve').selectedIndex].text;

		if(rider1Dorsal)
		{
			arrayDorsal.push(rider1Dorsal);
			arrayCyclists.push(rider1Name);
		}
		if(rider2Dorsal)
		{
			arrayDorsal.push(rider2Dorsal);
			arrayCyclists.push(rider2Name);
		}
		if(rider3Dorsal)
		{
			arrayDorsal.push(rider3Dorsal);
			arrayCyclists.push(rider3Name);
		}
		if(rider4Dorsal)
		{
			arrayDorsal.push(rider4Dorsal);
			arrayCyclists.push(rider4Name);
		}
		if(rider5Dorsal)
		{
			arrayDorsal.push(rider5Dorsal);
			arrayCyclists.push(rider5Name);
		}
		if(rider6Dorsal)
		{
			arrayDorsal.push(rider6Dorsal);
			arrayCyclists.push(rider6Name);
		}
		if(rider7Dorsal)
		{
			arrayDorsal.push(rider7Dorsal);
			arrayCyclists.push(rider7Name);
		}
		if(rider8Dorsal)
		{
			arrayDorsal.push(rider8Dorsal);
			arrayCyclists.push(rider8Name);
		}
		if(rider9Dorsal)
		{
			arrayDorsal.push(rider9Dorsal);
			arrayCyclists.push(rider9Name);
			
		}

		if(reserveDorsal)
		{

			arrayDorsal.push("");
			arrayCyclists.push("");

			arrayDorsal.push(reserveDorsal);
			arrayCyclists.push(reserveName);
		}



		if(arrayDorsal)
		{
		
			var arrayDorsalSorted = arrayDorsal.slice();

			arrayDorsalSorted.sort(function(a, b){return b-a});

			if(reserveDorsal)
			{
				arrayDorsalSorted.length = arrayDorsalSorted.length - 1;
			}


			for (i=0; i < arrayDorsalSorted.length - 1; i++)
			{
				if (arrayDorsalSorted[i] == arrayDorsalSorted[i+1])
				{
					document.getElementById('error').innerHTML = repeatedError;
					repeated = true;
					break;
				}
				else
				{
					repeated = false;

					if(document.getElementById('error').innerHTML == repeatedError)
					{
						document.getElementById('error').innerHTML = "";
					}
				}
			}

		}
	}

	function printDorsal(){

		document.getElementById('dorsalList').innerHTML = arrayDorsal.join("\n") + "\n\n" + arrayCyclists.join("\n");
	}

	function sendMail()
	{
		var divisionC = checkDivision();
		var userC = checkUser();
		var budgetC = checkBudget();
		var ridersC = checkRiders();
		var repeatedC = checkRepeated();

		if(divisionC == false || userC == false || budgetC == false || ridersC == false || repeatedC == false )
		{
			return;
		}
		else
		{
			var body = arrayDorsal.join("%0A") + "%0A%0A" + arrayCyclists.join("%0A");
	    	var subject = document.getElementById('user').value;
	    	var email = "grandesvueltasacb@hotmail.com";

	    	window.location.href = 'mailto:'+email+'?subject=Equipo%20Usuario:%20'+subject+'&body='+body;
		}
    }

    function checkDivision()
    {
    	if(credits < 1500)
    	{
    		alert(divError);
    		return false;
    	}
    }

    function checkUser()
    {
    	if(user.value == "")
    	{
    		alert(userError);
    		return false;
    	}
    }

    function checkBudget()
    {
 
    	if(remaining < 0)
    	{	
    		alert(budgetError);
    		return false;
    	}
    }

    function checkRiders()
    {
    	var price1 = parseInt(document.getElementById('rider1').value);
		var price2 = parseInt(document.getElementById('rider2').value);
		var price3 = parseInt(document.getElementById('rider3').value);
		var price4 = parseInt(document.getElementById('rider4').value);
		var price5 = parseInt(document.getElementById('rider5').value);
		var price6 = parseInt(document.getElementById('rider6').value);
		var price7 = parseInt(document.getElementById('rider7').value);
		var price8 = parseInt(document.getElementById('rider8').value);
		var price9 = parseInt(document.getElementById('rider9').value);

    	if( price1 == 0 || price2 == 0 || price3 == 0 || price4 == 0 || price5 == 0 || price6 == 0 || price7 == 0 || price8 == 0 || price9 == 0 )
    	{
    		alert("Lista de corredores incompleta.");
    		return false;
    	}
    }

    function checkRepeated()
    {
    	if(repeated == true)
    	{
    		alert(repeatedError);
    		return false;
    	}
    }

    function showProfiles()
    {
    	if(state == 0)
    	{
    		document.getElementById('profiles').style.display = "";
    		state = 1;
    	}
    	else
    	{
    		document.getElementById('profiles').style.display = "none";
    		state = 0;
    	}
    }

    function changeStage(stageValue)
    {
    	var profilePic = "profiles/Stage" + (parseInt(document.getElementById('stageNumber').value)) + ".jpg";
		document.getElementById('stages').src = profilePic;
    }

    function fullSize()
    {
		var image = document.getElementById('stages').src;

    	window.open(image, 'Perfil de etapa', "menubar=1,resizable=1,width=600,height=478");
    }

    function showRidersByPrice()
    {

    	if(state2 == 0)
    	{
    		document.getElementById('ridersByPriceTR').style.display = "";
    		state2 = 1;
    	}
    	else
    	{
    		document.getElementById('ridersByPriceTR').style.display = "none";
    		state2 = 0;
    	}

    }

</script> 
</center>
</body>
</html>
