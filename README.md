# Tutorial: Cum să instalez și să rulez aplicația offline pe calculatorul meu

## Ce este această aplicație?

Aceasta este o aplicație web pentru completarea automată a documentelor **ANEXA 1** și **ANEXA 2** - cereri pentru persoane cu handicap. Aplicația funcționează în browser și poate rula complet offline pe calculatorul dumneavoastră.

## De ce programe am nevoie?

Pentru a rula această aplicație pe calculatorul dumneavoastră, veți avea nevoie de:

1. **Node.js** - programul care face aplicația să funcționeze
2. **Git** - programul pentru descărcarea codului aplicației
3. **Un browser web** - Chrome, Firefox, Safari, sau Edge
4. **Un editor de text** (opțional) - pentru a vedea codul

## Pas 1: Instalarea Node.js

### Pentru Windows:

1. Mergeți pe site-ul oficial: **https://nodejs.org**
2. Descărcați versiunea **LTS** (versiunea recomandată) - va fi un fișier cu numele similar cu `node-v20.x.x-x64.msi`
3. Rulați fișierul descărcat și urmați instrucțiunile de instalare
4. Apăsați **Next** → **Next** → **Install** → **Finish**
5. Restartați calculatorul

### Pentru Mac:

1. Mergeți pe site-ul oficial: **https://nodejs.org**
2. Descărcați versiunea **LTS** pentru Mac - va fi un fișier `.pkg`
3. Deschideți fișierul descărcat și urmați instrucțiunile
4. Introduceți parola de administrator când vi se cere
5. Restartați calculatorul

### Pentru Linux (Ubuntu/Debian):

1. Deschideți **Terminal**
2. Copiați și lipiți această comandă:
   ```bash
   curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
   sudo apt-get install -y nodejs
   ```
3. Introduceți parola când vi se cere

## Pas 2: Instalarea Git

### Pentru Windows:

1. Mergeți pe: **https://git-scm.com/download/windows**
2. Descărcați fișierul (se va descărca automat)
3. Rulați fișierul și instalați cu setările implicite
4. Apăsați **Next** la toate opțiunile și **Install** la final

### Pentru Mac:

1. Mergeți pe: **https://git-scm.com/download/mac**
2. Descărcați fișierul pentru Mac
3. Instalați urmând instrucțiunile

### Pentru Linux:

Deschideți **Terminal** și tastați:
```bash
sudo apt-get update
sudo apt-get install git
```

## Pas 3: Verificarea instalării

Pentru a verifica că totul s-a instalat corect:

### Pe Windows:
1. Apăsați **Windows + R**
2. Tastați `cmd` și apăsați **Enter**
3. În fereastra neagră care se deschide, tastați:
   ```
   node --version
   ```
4. Ar trebui să vedeți ceva similar cu `v20.9.0`
5. Apoi tastați:
   ```
   git --version
   ```
6. Ar trebui să vedeți ceva similar cu `git version 2.42.0`

### Pe Mac:
1. Apăsați **Cmd + Spațiu**
2. Tastați `terminal` și apăsați **Enter**
3. Urmați aceiași pași ca pentru Windows (comenzile sunt identice)

### Pe Linux:
1. Deschideți **Terminal**
2. Urmați aceiași pași ca pentru Windows

**Important**: Dacă vedeți numere de versiuni, înseamnă că totul este instalat corect!

## Pas 4: Descărcarea aplicației

1. Creați un folder nou pe Desktop numit `Aplicatie-Documente`
2. Deschideți **Command Prompt** (Windows) sau **Terminal** (Mac/Linux)
3. Navigați către folder-ul creat:

   **Pe Windows:**
   ```
   cd Desktop\Aplicatie-Documente
   ```

   **Pe Mac/Linux:**
   ```
   cd Desktop/Aplicatie-Documente
   ```

4. Descărcați aplicația tastând:
   ```
   git clone [URL-ul aplicației] .
   ```
   
   **Notă**: Înlocuiți `[URL-ul aplicației]` cu link-ul real către aplicație pe GitHub.

5. **IMPORTANT**: După descărcare, verificați că aveți fișierul `package.json` în folder. Dacă nu îl aveți, recreați-l cu următorul conținut:

   Creați un fișier nou numit `package.json` și copiați conținutul din secțiunea "Conținut package.json" de mai jos.

## Pas 5: Instalarea dependințelor

În aceeași fereastră de comandă, tastați:

```
npm install
```

**Ce se întâmplă**: Această comandă descarcă toate bibliotecile de care aplicația are nevoie. Procesul poate dura 2-5 minute.

**Când e gata**: Veți vedea că nu mai apar mesaje și cursorul revine la prompt.

## Pas 6: Pornirea aplicației

Pentru a porni aplicația, tastați una din următoarele comenzi:

```
npm start
```

**SAU**

```
npm run dev
```

**IMPORTANT**: Nu folosiți comanda `npm run db:push` - aceasta nu este necesară pentru această aplicație!

**Ce se întâmplă**:
- Se va afișa text în fereastră similar cu "Starting development server..."
- După 30-60 de secunde, browserul se va deschide automat la adresa `http://localhost:3000`
- Dacă browserul nu se deschide automat, deschideți-l manual și accesați: **http://localhost:3000**

## Pas 7: Utilizarea aplicației

Odată ce aplicația s-a deschis în browser:

1. **Adăugați persoane**: Folosiți butonul "Adaugă persoană nouă" pentru a introduce datele
2. **Selectați tipul de document**: Alegeți între ANEXA 1 sau ANEXA 2
3. **Completați documentul**: Selectați persoana din listă pentru completarea automată
4. **Salvați PDF**: Folosiți butonul "Salvează PDF" pentru a descărca documentul

## Cum opresc aplicația?

Pentru a opri aplicația:
1. Mergeți în fereastra de comandă unde rulează aplicația
2. Apăsați **Ctrl + C** (pe toate sistemele de operare)
3. Confirmați cu **Y** dacă vi se cere

## Cum pornesc aplicația din nou?

Pentru a porni aplicația din nou:
1. Deschideți **Command Prompt** sau **Terminal**
2. Navigați către folder-ul aplicației:
   ```
   cd Desktop/Aplicatie-Documente
   ```
3. Rulați una din aceste comenzi:
   ```
   npm start
   ```
   **SAU**
   ```
   npm run dev
   ```

**Atenție**: Nu folosiți comenzi ca `npm run db:push`, `npm run db:migrate` sau alte comenzi cu "db:" - acestea nu sunt necesare!

## Probleme comune și soluții

### "npm error Missing script: db:push" sau comenzi similare cu "db:"
- **Explicație**: Această aplicație NU folosește o bază de date externă! Toate datele se salvează local în browser.
- **Soluție**: Folosiți doar `npm start` sau `npm run dev` pentru a porni aplicația.

### "node is not recognized" sau "command not found"
- **Soluție**: Node.js nu s-a instalat corect. Reinstalați Node.js și restartați calculatorul.

### "npm install" nu funcționează
- **Soluție**: Verificați conexiunea la internet. Încercați din nou după câteva minute.

### Aplicația nu se deschide în browser
- **Soluție**: Deschideți manual browserul și accesați: **http://localhost:3000**

### "Port 3000 is already in use"
- **Soluție**: Închideți toate ferestrele de browser și programele care ar putea folosi portul 3000, apoi încercați din nou.

## Funcționare offline

**Odată instalată, aplicația funcționează complet offline!**

- Nu aveți nevoie de internet pentru a o folosi
- Toate datele se salvează local pe calculatorul dumneavoastră
- PDF-urile se generează local, fără să trimiteți informații pe internet

## Backup-ul datelor

Datele persoanelor se salvează automat în browser. Pentru siguranță:

1. **Exportați datele periodic** folosind opțiunile din aplicație
2. **Faceți backup la folder-ul aplicației** copiind întregul folder `Aplicatie-Documente`

## Actualizarea aplicației

Pentru a primi actualizări:

1. Deschideți **Command Prompt** sau **Terminal**
2. Navigați către folder-ul aplicației
3. Tastați:
   ```
   git pull
   npm install
   ```

## Suport tehnic

Pentru probleme tehnice sau întrebări:
- Verificați că ați urmat toți pașii în ordine
- Restartați calculatorul și încercați din nou
- Contactați persoana care v-a furnizat aplicația

## Despre stocarea datelor

**IMPORTANT**: Această aplicație nu folosește o bază de date externă!

- Toate datele persoanelor se salvează automat în **localStorage** (memoria browserului)
- Nu există comenzi de tip `npm run db:push` sau `npm run db:migrate`
- Nu aveți nevoie să configurați nicio bază de date
- Aplicația funcționează complet offline după prima instalare

## Comenzile corecte pentru această aplicație

✅ **Comenzi CORECTE** (folosiți acestea):
- `npm install` - pentru instalarea dependințelor
- `npm start` - pentru pornirea aplicației
- `npm run dev` - alternativă pentru pornirea aplicației

❌ **Comenzi GREȘITE** (NU le folosiți):
- `npm run db:push` - NU există în această aplicație
- `npm run db:migrate` - NU există în această aplicație
- `npm run db:seed` - NU există în această aplicație

## Conținut package.json

Dacă fișierul `package.json` nu există sau este gol, creați-l cu următorul conținut:

```json
{
  "name": "anexa-documente-app",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "start": "vite",
    "build": "tsc && vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "lucide-react": "^0.263.1",
    "@radix-ui/react-slot": "^1.0.2",
    "@radix-ui/react-dialog": "^1.0.4",
    "@radix-ui/react-select": "^1.2.2",
    "@radix-ui/react-checkbox": "^1.0.4",
    "@radix-ui/react-alert-dialog": "^1.0.4",
    "@radix-ui/react-dropdown-menu": "^2.0.5",
    "@radix-ui/react-label": "^2.0.2",
    "@radix-ui/react-popover": "^1.0.6",
    "@radix-ui/react-separator": "^1.0.3",
    "@radix-ui/react-toast": "^1.1.4",
    "@radix-ui/react-tooltip": "^1.0.6",
    "class-variance-authority": "^0.7.0",
    "clsx": "^2.0.0",
    "tailwind-merge": "^1.14.0",
    "date-fns": "^2.30.0",
    "react-day-picker": "^8.8.2"
  },
  "devDependencies": {
    "@types/react": "^18.2.15",
    "@types/react-dom": "^18.2.7",
    "@typescript-eslint/eslint-plugin": "^6.0.0",
    "@typescript-eslint/parser": "^6.0.0",
    "@vitejs/plugin-react": "^4.0.3",
    "eslint": "^8.45.0",
    "eslint-plugin-react-hooks": "^4.6.0",
    "eslint-plugin-react-refresh": "^0.4.3",
    "typescript": "^5.0.2",
    "vite": "^4.4.5",
    "tailwindcss": "^4.0.0"
  }
}
```

## Structura de fișiere necesară

După instalare, proiectul ar trebui să aibă următoarea structură:

```
Aplicatie-Documente/
├── src/
│   ├── App.tsx
│   └── main.tsx
├── components/
│   ├── Anexa1.tsx
│   ├── Document.tsx
│   ├── DocumentForm.tsx
│   ├── PersonManager.tsx
│   └── ui/
├── styles/
│   └── globals.css
├── index.html
├── package.json
├── vite.config.ts
└── README.md
```

---

**Notă importantă**: Această aplicație respectă complet confidențialitatea. Toate datele rămân pe calculatorul dumneavoastră și nu sunt trimise nicăieri pe internet.