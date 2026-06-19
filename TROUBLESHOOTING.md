# Troubleshooting

## Error: `ModuleNotFoundError: No module named 'sklearn'`

Artinya Streamlit berjalan di environment Python yang belum memiliki `scikit-learn`.

Pada mesin ini, traceback menunjukkan Streamlit memakai:

```text
C:\Users\Ryzen5\AppData\Local\Programs\Python\Python314\
```

Untuk model pickle machine learning, gunakan Python 3.11 atau 3.12 agar dependency seperti `scikit-learn`, `xgboost`, dan `lightgbm` lebih aman.

## Solusi yang disarankan

1. Install Python 3.11 dari:

```text
https://www.python.org/downloads/release/python-3119/
```

Saat install, centang `Add python.exe to PATH`.

2. Buka terminal VS Code di folder proyek ini.

3. Buat ulang virtual environment dengan Python 3.11:

```powershell
py -3.11 -m venv .venv
```

4. Aktifkan virtual environment:

```powershell
.\.venv\Scripts\Activate.ps1
```

5. Pastikan Python sudah dari `.venv`:

```powershell
python --version
where python
```

`where python` harus menampilkan path `.venv\Scripts\python.exe` di baris pertama.

6. Install dependency:

```powershell
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

7. Jalankan Streamlit:

```powershell
python -m streamlit run app.py
```

## Jika PowerShell menolak aktivasi venv

Jalankan:

```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

Lalu aktifkan ulang:

```powershell
.\.venv\Scripts\Activate.ps1
```

## Alternatif sementara

Jika tetap ingin memakai Python 3.14 global, jalankan:

```powershell
python -m pip install scikit-learn joblib pandas streamlit xgboost lightgbm
python -m streamlit run app.py
```

Namun opsi ini kurang disarankan untuk deployment model pickle karena kompatibilitas package ML lebih berisiko.
