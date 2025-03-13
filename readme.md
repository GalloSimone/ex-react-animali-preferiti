Il tuo collega, probabilmente distratto da un gatto o un pappagallo, ha creato una pagina HTML statica invece di utilizzare React come richiesto. La pagina è già online, quindi non possiamo rifarla da zero. Ora tocca a te trasformarla in una meraviglia interattiva usando React, direttamente all’interno del documento HTML. Segui le milestone e dimostra che anche un errore può diventare un’opportunità per brillare!

<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>I miei animali Preferiti</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
      <h1>I miei animali Preferiti</h1>
    </header>
    <main>
        <figure>
            <img src="https://picsum.photos/400/300" alt="Immagine Casuale">
        </figure>
        <div class="lista-animali"></div>
    </main>
      <footer>
      <p>Creato con amore da... un collega sbadato! 🐾</p>
    </footer>
  </body>
</html>
​

body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
header {
    background-color: #333;
    color: white;
    text-align: center;
    padding: 1rem;
}
main {
    padding: 1rem;
    display: flex;
    flex-direction: column;
    align-items: center;
}
footer {
    background-color: #333;
    color: white;
    text-align: center;
    padding: 1rem;
}
form{
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
}
img{
    max-width: 100%;
}
.lista-animali{
    width: 100%;
}
📌 Milestone 1: Inserire un Componente React

Monta un componente React all’interno dell’elemento con classe .lista-animali.

Il componente deve includere:
Un elemento <details> con titolo "Animali", che contiene:
Una lista <ul> statica che viene creata a partire da un array di stringhe (animals) dove ciascuna stringa rappresenta il nome di un animale.

Obiettivo: Mostrare la struttura base della lista di animali con un <details> che può essere espanso o contratto.
📌 Milestone 2: Aggiungere Animali Casuali

Trasforma l’array animals usando useState (l’array è inizialmente vuoto).
Aggiungi un bottone "Aggiungi Animale" sopra il <details>.
Cliccando il bottone, un animale casuale viene aggiunto alla lista.
Usa un array predefinito per scegliere casualmente:

const animalsChoices = ["Cane", "Gatto", "Pappagallo", "Cavallo", "Panda"];
L’animale selezionato deve essere aggiunto all’interno della lista <ul> come <li>.

Obiettivo: L’utente può vedere gli animali aggiunti dinamicamente nella lista.
📌 Milestone 3: Usare una Modale per Aggiungere Animali

Partendo da questo componente Modal:

function Modal({
      title, 
      content, 
      show = false, 
      onClose = () => {}
  }){
      return show && ReactDOM.createPortal(
          <div className="modal-container">
              <div className="modal">
                  <h2>{title}</h2>
                  <p>{content}</p>
                  <button onClick={onClose}>Annulla</button>
              </div>
          </div>,
          document.body
      )
  }

.modal-container{
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.75);
    display: flex;
    justify-content: center;
    align-items: center;
}
.modal{
    background-color: white;
    padding: 20px;
    border-radius: 5px;
}
Espandilo affinché:
La vecchia prop content può essere usata per passare un componente qualsiasi.
Un nuovo div in fondo alla modale contiene il bottone Annulla e un nuovo bottone Conferma.
Una nuova prop onConfirm si aspetta una funzione per gestire l’azione di conferma.
Sostituisci l’aggiunta casuale dell’animale con una modale interattiva:
Cliccando il bottone "Aggiungi Animale," si apre una modale.
La modale include un input di testo (passato al prop content) per inserire il nome di un animale.
Conferma: Aggiunge l’animale alla lista e chiude la modale.
Annulla: Chiude la modale senza modificare la lista.

Obiettivo: L’utente può aggiungere animali specifici utilizzando la modale.