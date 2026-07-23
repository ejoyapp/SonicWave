<!-- LANGUAGE SWITCHER -->
<p align="center">
  <a href="#-简体中文">简体中文</a> ·
  <a href="#-english">English</a> ·
  <a href="#-deutsch">Deutsch</a> ·
  <a href="#-français">Français</a> ·
  <a href="#-한국어">한국어</a> ·
  <a href="#-日本語">日本語</a>
</p>

> 点击上方语言跳转到对应版本。Click a language above to jump to that version.

---

<a id="-简体中文"></a>

## 🇨🇳 简体中文

[English](#-english) · [Deutsch](#-deutsch) · [Français](#-français) · [한국어](#-한국어) · [日本語](#-日本語)

本应用的 AI 模型支持两种运行时：

- **WASM**（如 RNNoise）：浏览器内 AudioWorklet 执行，实时逐帧，无需 Python。
- **Python**（如 DeepFilterNet、未来的 Whisper、TTS）：主进程 spawn 一个 Python 子进程（sidecar），通过 stdin/stdout 的 JSON 协议通信。这是 Electron + Python 的业界标准做法（Ollama、LM Studio 同类架构）。

Python 模型适合**批处理**场景（录音后处理、导出降噪、音频转写、语音合成），实时逐帧降噪仍由 WASM 引擎承担。

### 一、准备 Python 3.10 环境

DeepFilterNet 对 Python 3.8~3.11 支持较好，推荐 **3.10**。

**方式 A：系统 Python（最简单）**

```bash
# macOS (Homebrew)
brew install python@3.10
# Ubuntu/Debian
sudo apt install python3.10 python3.10-venv
# Windows：从 python.org 下载 3.10.x 安装包，勾选 "Add to PATH"
```

**方式 B：独立虚拟环境（推荐，隔离依赖）**

```bash
python3.10 -m venv ~/.audiosampler-py
source ~/.audiosampler-py/bin/activate   # Windows: ~\.audiosampler-py\Scripts\activate
```

### 二、安装模型依赖

```bash
pip install deepfilternet torch numpy
# 仅 CPU 推理可装 CPU 版 torch(体积更小)：
pip install torch --index-url https://download.pytorch.org/whl/cpu
```

首次运行时 DeepFilterNet 会自动下载权重（约 20MB）。

### 三、在应用内配置

1. 打开 AI 降噪行的 ⚙ → **Python 设置**
2. 填入 Python 可执行文件路径（系统：`/usr/bin/python3.10`，虚拟环境：`~/.audiosampler-py/bin/python`，Windows：`C:\Python310\python.exe`）
3. 点 **检测** 确认版本（应显示 `Python 3.10.x`）
4. 保存后回到模型列表，DeepFilterNet 卡片点 **使用**

---

<a id="-english"></a>

## 🇬🇧 English

[简体中文](#-简体中文) · [Deutsch](#-deutsch) · [Français](#-français) · [한국어](#-한국어) · [日本語](#-日本語)

This app's AI models support two runtimes:

- **WASM** (e.g. RNNoise): runs in-browser via AudioWorklet, real-time per-frame, no Python needed.
- **Python** (e.g. DeepFilterNet, future Whisper, TTS): the main process spawns a Python subprocess (sidecar) communicating via a stdin/stdout JSON protocol — the industry-standard Electron + Python approach (same as Ollama, LM Studio).

Python models suit **batch** scenarios (post-recording processing, export denoise, transcription, voice synthesis); real-time per-frame denoise stays on the WASM engine.

### 1. Prepare a Python 3.10 environment

DeepFilterNet works best with Python 3.8–3.11; **3.10** is recommended.

**Option A: system Python (simplest)**

```bash
# macOS (Homebrew)
brew install python@3.10
# Ubuntu/Debian
sudo apt install python3.10 python3.10-venv
# Windows: download the 3.10.x installer from python.org, check "Add to PATH"
```

**Option B: isolated virtualenv (recommended)**

```bash
python3.10 -m venv ~/.audiosampler-py
source ~/.audiosampler-py/bin/activate   # Windows: ~\.audiosampler-py\Scripts\activate
```

### 2. Install model dependencies

```bash
pip install deepfilternet torch numpy
# CPU-only inference can use the smaller CPU torch build:
pip install torch --index-url https://download.pytorch.org/whl/cpu
```

DeepFilterNet auto-downloads its weights (~20MB) on first run.

### 3. Configure inside the app

1. Open the ⚙ on the AI denoise row → **Python Settings**
2. Enter the Python executable path (system: `/usr/bin/python3.10`, venv: `~/.audiosampler-py/bin/python`, Windows: `C:\Python310\python.exe`)
3. Click **Probe** to confirm the version (should show `Python 3.10.x`)
4. Save, return to the model list, and click **Use** on the DeepFilterNet card

---

<a id="-deutsch"></a>

## 🇩🇪 Deutsch

[简体中文](#-简体中文) · [English](#-english) · [Français](#-français) · [한국어](#-한국어) · [日本語](#-日本語)

Die KI-Modelle dieser App unterstützen zwei Laufzeiten:

- **WASM** (z. B. RNNoise): läuft im Browser via AudioWorklet, echtzeitfähig pro Frame, ohne Python.
- **Python** (z. B. DeepFilterNet, künftig Whisper, TTS): Der Hauptprozess startet einen Python-Subprozess (Sidecar), der über ein stdin/stdout-JSON-Protokoll kommuniziert — der Industriestandard für Electron + Python (wie Ollama, LM Studio).

Python-Modelle eignen sich für **Batch**-Szenarien (Nachbearbeitung von Aufnahmen, Export-Entrauschen, Transkription, Sprachsynthese); Echtzeit-Entrauschen pro Frame bleibt bei der WASM-Engine.

### 1. Python-3.10-Umgebung vorbereiten

DeepFilterNet funktioniert am besten mit Python 3.8–3.11; **3.10** wird empfohlen.

**Option A: System-Python (am einfachsten)**

```bash
# macOS (Homebrew)
brew install python@3.10
# Ubuntu/Debian
sudo apt install python3.10 python3.10-venv
# Windows: 3.10.x-Installer von python.org, "Add to PATH" ankreuzen
```

**Option B: isolierte virtuelle Umgebung (empfohlen)**

```bash
python3.10 -m venv ~/.audiosampler-py
source ~/.audiosampler-py/bin/activate   # Windows: ~\.audiosampler-py\Scripts\activate
```

### 2. Modellabhängigkeiten installieren

```bash
pip install deepfilternet torch numpy
# Reine CPU-Inferenz kann das kleinere CPU-torch nutzen:
pip install torch --index-url https://download.pytorch.org/whl/cpu
```

DeepFilterNet lädt seine Gewichte (~20 MB) beim ersten Start automatisch herunter.

### 3. In der App konfigurieren

1. ⚙ in der KI-Entrausch-Zeile öffnen → **Python-Einstellungen**
2. Python-Pfad eingeben (System: `/usr/bin/python3.10`, venv: `~/.audiosampler-py/bin/python`, Windows: `C:\Python310\python.exe`)
3. **Prüfen** klicken, um die Version zu bestätigen (sollte `Python 3.10.x` zeigen)
4. Speichern, zur Modellliste zurückkehren und auf der DeepFilterNet-Karte **Nutzen** klicken

---

<a id="-français"></a>

## 🇫🇷 Français

[简体中文](#-简体中文) · [English](#-english) · [Deutsch](#-deutsch) · [한국어](#-한국어) · [日本語](#-日本語)

Les modèles IA de cette application prennent en charge deux runtimes :

- **WASM** (ex. RNNoise) : s'exécute dans le navigateur via AudioWorklet, en temps réel image par image, sans Python.
- **Python** (ex. DeepFilterNet, futurs Whisper, TTS) : le processus principal lance un sous-processus Python (sidecar) communiquant via un protocole JSON stdin/stdout — l'approche standard pour Electron + Python (comme Ollama, LM Studio).

Les modèles Python conviennent aux scénarios **par lots** (post-traitement d'enregistrement, débruitage à l'export, transcription, synthèse vocale) ; le débruitage temps réel image par image reste sur le moteur WASM.

### 1. Préparer un environnement Python 3.10

DeepFilterNet fonctionne mieux avec Python 3.8–3.11 ; **3.10** est recommandé.

**Option A : Python système (le plus simple)**

```bash
# macOS (Homebrew)
brew install python@3.10
# Ubuntu/Debian
sudo apt install python3.10 python3.10-venv
# Windows : installateur 3.10.x depuis python.org, cocher "Add to PATH"
```

**Option B : environnement virtuel isolé (recommandé)**

```bash
python3.10 -m venv ~/.audiosampler-py
source ~/.audiosampler-py/bin/activate   # Windows : ~\.audiosampler-py\Scripts\activate
```

### 2. Installer les dépendances du modèle

```bash
pip install deepfilternet torch numpy
# L'inférence CPU seule peut utiliser le torch CPU plus léger :
pip install torch --index-url https://download.pytorch.org/whl/cpu
```

DeepFilterNet télécharge automatiquement ses poids (~20 Mo) au premier lancement.

### 3. Configurer dans l'application

1. Ouvrez le ⚙ sur la ligne de débruitage IA → **Paramètres Python**
2. Saisissez le chemin de l'exécutable Python (système : `/usr/bin/python3.10`, venv : `~/.audiosampler-py/bin/python`, Windows : `C:\Python310\python.exe`)
3. Cliquez sur **Tester** pour confirmer la version (doit afficher `Python 3.10.x`)
4. Enregistrez, revenez à la liste des modèles et cliquez sur **Utiliser** sur la carte DeepFilterNet

---

<a id="-한국어"></a>

## 🇰🇷 한국어

[简体中文](#-简体中文) · [English](#-english) · [Deutsch](#-deutsch) · [Français](#-français) · [日本語](#-日本語)

이 앱의 AI 모델은 두 가지 런타임을 지원합니다:

- **WASM**(예: RNNoise): 브라우저 내 AudioWorklet으로 실행, 실시간 프레임 단위, Python 불필요.
- **Python**(예: DeepFilterNet, 향후 Whisper, TTS): 메인 프로세스가 Python 하위 프로세스(사이드카)를 생성하여 stdin/stdout JSON 프로토콜로 통신 — Electron + Python의 업계 표준 방식(Ollama, LM Studio와 동일).

Python 모델은 **배치** 시나리오(녹음 후처리, 내보내기 노이즈 제거, 전사, 음성 합성)에 적합하며, 실시간 프레임 단위 노이즈 제거는 WASM 엔진이 담당합니다.

### 1. Python 3.10 환경 준비

DeepFilterNet은 Python 3.8–3.11에서 가장 잘 작동하며 **3.10**을 권장합니다.

**옵션 A: 시스템 Python(가장 간단)**

```bash
# macOS (Homebrew)
brew install python@3.10
# Ubuntu/Debian
sudo apt install python3.10 python3.10-venv
# Windows: python.org에서 3.10.x 설치 관리자 다운로드, "Add to PATH" 체크
```

**옵션 B: 격리된 가상 환경(권장)**

```bash
python3.10 -m venv ~/.audiosampler-py
source ~/.audiosampler-py/bin/activate   # Windows: ~\.audiosampler-py\Scripts\activate
```

### 2. 모델 종속성 설치

```bash
pip install deepfilternet torch numpy
# CPU 전용 추론은 더 작은 CPU torch를 사용할 수 있습니다:
pip install torch --index-url https://download.pytorch.org/whl/cpu
```

DeepFilterNet은 첫 실행 시 가중치(~20MB)를 자동으로 다운로드합니다.

### 3. 앱 내에서 구성

1. AI 노이즈 제거 행의 ⚙ → **Python 설정** 열기
2. Python 실행 파일 경로 입력(시스템: `/usr/bin/python3.10`, venv: `~/.audiosampler-py/bin/python`, Windows: `C:\Python310\python.exe`)
3. **확인**을 클릭하여 버전 확인(`Python 3.10.x` 표시되어야 함)
4. 저장 후 모델 목록으로 돌아가 DeepFilterNet 카드에서 **사용** 클릭

---

<a id="-日本語"></a>

## 🇯🇵 日本語

[简体中文](#-简体中文) · [English](#-english) · [Deutsch](#-deutsch) · [Français](#-français) · [한국어](#-한국어)

本アプリの AI モデルは 2 つのランタイムをサポートします：

- **WASM**（例：RNNoise）：ブラウザ内で AudioWorklet として実行、リアルタイムのフレーム単位、Python 不要。
- **Python**（例：DeepFilterNet、将来の Whisper、TTS）：メインプロセスが Python サブプロセス（サイドカー）を起動し、stdin/stdout の JSON プロトコルで通信 — Electron + Python の業界標準手法（Ollama、LM Studio と同様）。

Python モデルは**バッチ**シナリオ（録音後処理、エクスポート時のノイズ除去、文字起こし、音声合成）に適し、リアルタイムのフレーム単位ノイズ除去は WASM エンジンが担当します。

### 1. Python 3.10 環境の準備

DeepFilterNet は Python 3.8～3.11 で最も良く動作し、**3.10** を推奨します。

**方法 A：システム Python（最も簡単）**

```bash
# macOS (Homebrew)
brew install python@3.10
# Ubuntu/Debian
sudo apt install python3.10 python3.10-venv
# Windows：python.org から 3.10.x インストーラーをダウンロードし "Add to PATH" にチェック
```

**方法 B：独立した仮想環境（推奨）**

```bash
python3.10 -m venv ~/.audiosampler-py
source ~/.audiosampler-py/bin/activate   # Windows: ~\.audiosampler-py\Scripts\activate
```

### 2. モデル依存関係のインストール

```bash
pip install deepfilternet torch numpy
# CPU のみの推論はより小さい CPU 版 torch を使用できます：
pip install torch --index-url https://download.pytorch.org/whl/cpu
```

DeepFilterNet は初回起動時に重み（約 20MB）を自動ダウンロードします。

### 3. アプリ内で設定

1. AI ノイズ除去行の ⚙ →**Python 設定**を開く
2. Python 実行ファイルのパスを入力（システム：`/usr/bin/python3.10`、venv：`~/.audiosampler-py/bin/python`、Windows：`C:\Python310\python.exe`）
3. **検出**をクリックしてバージョンを確認（`Python 3.10.x` と表示されるはず）
4. 保存してモデル一覧に戻り、DeepFilterNet カードで**使用**をクリック

