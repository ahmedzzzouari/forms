<!DOCTYPE html>
<head>

    <title>maison d'hote</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: hsla(46, 46%, 34%, 0.606);
        }

        h1, h3 {
            text-align: center;
        }

        form {
            max-width: 400px;
            margin: 0 auto;
        }

        label {
            display: block;
            margin-bottom: 5px;
        }

        input, select {
            width: 100%;
            padding: 8px;
            margin-bottom: 10px;
            box-sizing: border-box;
        }

        input[type="button"] {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 10px 15px;
            text-align: center;
            text-decoration: none;
            display: inline-block;
            font-size: 16px;
            margin-bottom: 20px;
            cursor: pointer;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }

        table, th, td {
            border: 1px solid #ddd;
        }

        th, td {
            padding: 10px;
            text-align: left;
        }

        th {
            background-color: #4CAF50;
            color: white;
        }
    </style>
</head>
<body>
    <h1>bienvenue dans notre maison d'hôte</h1>
    <h3>remplissez ce formulaire pour faire une réservation</h3>
    <script>
            function reserver() {
                if (F1.nom.value == "" || F1.email.value == "" || F1.pays.value == "tous" || F1.datee.value == "" || F1.dates.value == "" || numtel == "") {
               alert("Veuillez remplir tous les champs du formulaire.");
               return false ;
                }
                var datenow =  Date.now();
                var dateentree = new Date(F1.datee.value);
                var datesortie = new Date(F1.dates.value);
                
                if (datesortie <= dateentree || isNaN(dateentree) || isNaN(datesortie)|| dateentree<=datenow) {
                    alert("Erreur de date ");
                    return false;
                }
                var difference = datesortie - dateentree;
                var differenceenjours = difference / (1000 * 60 * 60 * 24);
                var numtel = F1.telephone.value;
                if (numtel.length != 8 || isNaN(numtel) ) {
                    alert("la numero de telephone est incorrect");
                    return false ; 
                }
                var tableaureservation = [
                    ["nom complet :", F1.nom.value],
                    ["adresse email :", F1.email.value],
                    ["pays :", F1.pays.value],
                    ["date d'entree :", F1.datee.value],
                    ["date de sortie :", F1.dates.value],
                    ["numero de telephone :", F1.telephone.value],
                    ["jours reserves :", differenceenjours],
                    ["type de chambre :", F1.choix.value]
                ];
                document.write("<h2> merci pour votre reservation </h2>");
                afficher(tableaureservation);
            }

            function afficher(table) {
                document.write('<table border="1"><tr >');
                for (var i = 0; i < table.length; i++) {
                    document.write('<td>' + table[i].join(' ') + '</td>');
                }
                document.write('</tr></table>');
            }
            function choixi(b){
              if(b.choix[0].checked){ alert("voux avez choisi  " + b.choix[0].value );}
              if(b.choix[1].checked){ alert("voux avez choisi  " + b.choix[1].value );}
              if(b.choix[2].checked){ alert("voux avez choisi  " + b.choix[2].value );}

            }
            
    </script>   

    </script>

    <form name="F1">

        <label form="fname">nom complet:</label><br>
        <input type="text" name="nom" value="" required><br>
        <label form="mail">adresse email :</label> <br>
        <input type="email" name="email" value=""> <br>
        <label for="pays"> pays :</label> <br>
        <select name="pays">
            <option value="tous">choisir votre pays</option>
            <option value="tunisie">tunisie</option>
            <option value="algerie">Algerie</option>
            <option value="libye">libye</option>
            <option value="autres">autres</option>
        </select> <br>
        <label form="date">La date d'entree</label><br>
        <input type="date" name="datee" value=""> <br>
        <label form="date">La date de sortie</label><br>
        <input type="date" name="dates" value=""> <br>
        <label for="telephone">Numero de telephone (8 chiffres) :</label><br>
        <input type="tel" id="telephone" name="telephone" pattern="[0-9]{8}" required>
        <br> <br>
        chambre a choisir:
        <br> <br>
        chambre pour 1 personne<br>
        <input type="radio" name="choix" value="chambre pour 1 personne">
        chambre pour 2 personne<br>
        <input type="radio" name="choix" value="chambre pour 2 personne">
        chambre pour 4 personne<br>
        <input type="radio" name="choix" value="chambre pour 4 personne">
        <input type ="button" name="choisi" value="quel est votre choix ?"  onclick="choixi(F1)">

        <br>
        <br>
        <input type="button" name="reserver1" value="reservation" onclick="reserver()">

    </form>

</body>
</html>
