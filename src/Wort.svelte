<script>
    import { onMount } from 'svelte';
  
    let jsonPath = '/public/worte.json'; // CSV-Dateipfad als Prop
  
    let words = $state([]); // Wörter aus der CSV-Datei"
    let currentWord = $state(''); // Aktuelles Wort
    let currentBeispiel = $state(''); // Aktuelles Beispiel
  
    // JSON-Datei einlesen
    onMount(async () => {
        const response = await fetch(jsonPath);
        const data = await response.json();
        words = data; // Wörter aus der JSON-Datei
        showRandomWord();
    });
    $inspect(words);
    // Zufälliges Wort anzeigen
    function showRandomWord() {
      if (words.length > 0) {
        let randomIndex = Math.floor(Math.random() * words.length);
        currentWord = words[randomIndex].Wort;
        currentBeispiel = words[randomIndex].Hoerbeispiel;
      }
    }
  </script>
  
  <div class="content">
    <h1>{currentWord}</h1>
    <button onclick={showRandomWord}>Zufälliges neues Wort</button>
    <br>
    <a href={currentBeispiel} target="_blank" rel="noopener noreferrer">Hörbeispiel</a>
  </div>
  
  <style>
    .content {
      text-align: center;
      color: white;
        z-index: 2;
    }
  
    button {
      font-size: 1rem;
      background-color: #003566;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    a {
      display: inline-block;
      margin-top: 1em;
      padding: 0.5em 1em;
      font-size: 1rem;
      background-color: #003566;
      color: white;
      text-decoration: none;
      border-radius: 5px;
    }
    a:hover {
      background-color: #001d3d;
    }
  
    button:hover {
      background-color: #001d3d;
    }
  </style>