@echo off
echo ================================
echo    Instalando Agente IA Local
echo ================================

echo.
echo [1/3] Descargando motor llama.cpp...
curl -L "https://github.com/ggml-org/llama.cpp/releases/download/b11583/llama-b11583-bin-win-vulkan-x64.zip" -o llama.zip

echo Extrayendo...
tar -xf llama.zip
del llama.zip

echo.
echo [2/3] Descargando modelo IA (4.5 GB, puede tardar varios minutos)...
curl -L "https://huggingface.co/lmstudio-community/Meta-Llama-3-8B-Instruct-GGUF/resolve/main/Meta-Llama-3-8B-Instruct-Q4_K_M.gguf?download=true" -o modelo.gguf

echo.
echo [3/3] Desbloqueando y iniciando agente...
powershell -Command "Unblock-File -Path 'agente_local.exe'; Unblock-File -Path 'modelo.gguf'"
start agente_local.exe

echo.
echo Espera el pitido agudo, la IA esta lista.
echo Ctrl+Alt+Z para usar / Ctrl+Alt+Q para cerrar.
pause
