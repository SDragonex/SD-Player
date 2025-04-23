# SD-Player

# 🎧 Roadmapa: Hudební přehrávač v C# WPF (.NET Framework)

Tento dokument popisuje detailní kroky k vytvoření plnohodnotného desktopového hudebního přehrávače pomocí **C#**, **WPF** a **.NET Framework**. Cílem je vytvořit moderní, stabilní a rozšiřitelnou aplikaci pro přehrávání hudby s možností playlistu, ovládání hlasitosti, progres baru, a případně dalších funkcí jako equalizér nebo tmavý režim.

---

## 🔧 FÁZE 1: Založení projektu

### ✅ Krok 1: Nový projekt

- Visual Studio → `Nový projekt` → `WPF App (.NET Framework)`
- Doporučená verze: `.NET Framework 4.7.2` nebo novější
- Pojmenuj projekt např. `MusicPlayerApp`

### ✅ Krok 2: Struktura UI (XAML)

- Použij `Grid` pro rozložení
- Základní prvky:
  - `ListBox` – playlist
  - `Button` – Play / Pause / Stop / Další / Předchozí
  - `Slider` – hlasitost
  - `ProgressBar` – průběh skladby
  - `Label` – aktuální čas / celkový čas

---

## 🎶 FÁZE 2: Přehrávání hudby

### ✅ Krok 1: Instalace NAudio

```powershell
Install-Package NAudio
```

### ✅ Krok 2: Základní funkce

- `AudioFileReader`, `WaveOutEvent` z NAudio
- Funkce:
  - `Play()`, `Pause()`, `Stop()`
  - Načtení pomocí `OpenFileDialog`

### ✅ Krok 3: Přehrávání více formátů

- WAV, MP3 – nativní podpora
- FLAC, AAC – volitelně (přes pluginy/konverzi)

---

## 📂 FÁZE 3: Playlist a správa skladeb

### ✅ Krok 1: Načtení více souborů

- `OpenFileDialog` s `Multiselect = true`
- Přidání do `ObservableCollection<string>` pro binding do `ListBox`

### ✅ Krok 2: Double-click na skladbu

- Event handler → `PlaySelectedFile()`

### ✅ Krok 3: Automatické přehrání další skladby

- Při dohrání skladby → `MediaEnded` nebo detekce `PlaybackStopped`

---

## 🧠 FÁZE 4: Pokročilé funkce

### ✅ Progres a seek bar

- Timer (`DispatcherTimer`) pro aktualizaci UI
- Kliknutí na `Slider` pro seeknutí

### ✅ Zobrazení metadat

```powershell
Install-Package taglib
```

- Zobraz: název, autor, album, cover art

### ✅ Ovládání hlasitosti

- `volumeSlider.Value` propojen s `waveOut.Volume`

---

## 🎨 FÁZE 5: Uživatelské rozhraní (UI/UX)

### ✅ Styling

- Použij `ResourceDictionary` pro stylování
- Moderní vzhled: tmavé téma, rounded corner buttons, flat design

### ✅ Layout

- `Grid`, `DockPanel` pro rozložení
- `ViewBox` pro škálování celého UI

### ✅ Témata

- Světlé / Tmavé téma přepínatelné za běhu

---

## ✨ FÁZE 6: Vylepšení a bonusové funkce

### ✅ 🎚 Equalizer (přes NAudio DSP)

- Nastavení frekvenčních pásem (bass, mid, treble)
- Uložení presetů

### ✅ 🧲 Drag & Drop

- Přetažení souboru do okna přehrávače

### ✅ 🎵 Cover art

- Načtení obrázku z ID3 tagu (TagLib)
- Zobrazení jako pozadí / thumbnail

### ✅ 🔁 Režimy přehrávání

- Opakování skladby
- Náhodné přehrávání
- Loop celého playlistu

### ✅ 📁 Ukládání playlistu

- Export/Import M3U nebo JSON playlistů

### ✅ 📦 Minimalizace do tray

- Ikonka v oznamovací oblasti
- Pravý klik → rychlé ovládání

### ✅ ⌨️ Klávesové zkratky

- Mezera: Play/Pause
- Šipky: Seek dopředu/dozadu
- +/−: Změna hlasitosti

---

## ✅ FÁZE 7: Finalizace a distribuce

### ✅ Testování

- Odchycení výjimek (chybné soubory, chybějící kodeky)
- Kompatibilita s různými verzemi Windows

### ✅ Distribuce

- `.exe` build
- Instalátor (např. Inno Setup, WiX)
- ClickOnce (pro jednoduchou instalaci)

---

## 💡 Budoucí nápady a inspirace

- 🔊 Visualizace zvuku (FFT, spektrum)
- 🌐 Streamování internetových rádií
- 📡 DLNA podpora (sdílení na síti)
- 🧠 AI doporučování skladeb (vzdálená budoucnost)
- 📱 Mobilní ovládání (např. přes web server běžící v aplikaci)

---

## 📚 Použité knihovny

| Název   | Popis                                     |
| ------- | ----------------------------------------- |
| NAudio  | Zvuková knihovna pro .NET                 |
| TagLib# | Čtení a zápis metadat v audio souborech   |
| WPF     | Uživatelské rozhraní na platformě Windows |

---
