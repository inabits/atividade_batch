chcp 65001
@echo off 
title ATIVIDADE - SISTEMAS DE INFORMAÇÃO
color 0e
mode 65,30

:inicio
cls
echo.
echo  ╔═════════════════════════════════════════════════╗
echo  ║ ------------------- LOGIN --------------------- ║
echo  ║    [N] Nova conta                               ║
echo  ║    [L] Logar                                    ║
echo  ╚═════════════════════════════════════════════════╝
set /p op=Digite a opção desejada: 
if /i %op% == n (goto:gravar)
if /i %op% == l (goto:logar) else (
	echo.
	echo Opção inválida!
	echo.
	pause
	goto inicio)
	
:gravar
cls
echo.
echo  ═══════════════════ NOVA CONTA ═══════════════════
set /p usuario=Digite o nome de usuário: 
set /p email=Digite o email:
set /p senha=Digite uma senha:
echo  ══════════════════════════════════════════════════
if not exist login.txt (
	echo LISTA DE CONTAS CADASTRADAS >> login.txt)
	
	Findstr %email% login.txt
:: errorlevel == 0 (se existir o cpf na lista)
:: errorlevel == 1 (se não existir)
	if %Errorlevel% == 1 (
		echo [%usuario%],[%senha%] >> login.txt
		echo [%email%],[%senha%] >> login.txt
		echo.
		echo Conta criada com sucesso!
		echo.
		pause
		goto:inicio) else (
		cls
		echo.
		echo  ═══════════════════ NOVA CONTA ═══════════════════
		echo Cliente com e-mail "%email%" já cadastrado!
		echo.
		pause
		goto:inicio)

:logar
cls
echo.
echo  ═════════════════════ LOGIN ═════════════════════
set /p usermail=USUÁRIO ou E-MAIL:
set /p senha=SENHA:
echo  ═════════════════════════════════════════════════
	findstr /c:[%usermail%],[%senha%] login.txt 
	if %Errorlevel% == 1 (
		echo.
		echo Usuário ou senha incorretos!
		echo.
		pause
		goto:inicio) else (
			echo.
			cls
			echo.
			echo ═════════════════════ LOGIN ═════════════════════
			echo Conta logada com sucesso! 
			echo.
			pause
			goto:menu)
		
:menu
cls
echo.
echo  ╔═════════════════════════════════════════════════╗
echo  ║ --------------- MENU PRINCIPAL ---------------- ║
echo  ║   [P] Pacote office                             ║
echo  ║   [A] Aplicativos do windows                    ║
echo  ║   [S] Serviços de rede/diversos                 ║
echo  ║   [J] Jogos                                     ║
echo  ║   [G] Gerenciamento da máquina                  ║
echo  ║   [E] Encerrar sessão login                     ║
echo  ║   [F] Finalizar programa                        ║
echo  ╚═════════════════════════════════════════════════╝
set /p op=Digite a opção desejada: 
if /i %op% == p (goto:office)
if /i %op% == a (goto:appwindows)
if /i %op% == s (goto:servicos)
if /i %op% == j (goto:jogos)
if /i %op% == g (goto:gerenciamento)
if /i %op% == e (goto:encerrar)
if /i %op% == f (goto:finalizar) else (
	echo.
	echo Opção inválida! 
	echo.
	pause
	goto menu)
	
:office
cls
echo.
echo  ╔═════════════════════════════════════════════════╗
echo  ║ ---------------- PACOTE OFFICE ---------------- ║
echo  ║   [W] Executar o Word                           ║
echo  ║   [E] Executar o Excel                          ║
echo  ║   [P] Executar o PowerPoint                     ║
echo  ║   [A] Executar o Access                         ║
echo  ║   [R] Retornar ao menu                          ║
echo  ╚═════════════════════════════════════════════════╝
set /p op=Digite a opção desejada: 
if /i %op% == w (
    start winword.exe
    goto:office)
if /i %op% == e (
    start excel.exe
    goto:office)
if /i %op% == p (
    start powerpnt.exe
    goto:office)
if /i %op% == a (
    start msaccess.exe
    goto:office)
if /i %op% == r (goto:menu) else (
	echo.
	echo Opção inválida! 
	echo.
	pause
	goto:office)

:appwindows
cls
echo.
echo  ╔═════════════════════════════════════════════════╗
echo  ║ ------------ APLICATIVOS WINDOWS -------------- ║
echo  ║   [B] Bloco de Notas                            ║
echo  ║   [T] Teclado virtual                           ║
echo  ║   [P] Painel de Controle                        ║
echo  ║   [C] Calculadora                               ║
echo  ║   [W] Windows Explorer                          ║
echo  ║   [R] Retornar ao menu                          ║
echo  ╚═════════════════════════════════════════════════╝
set /p op=Digite a opção desejada: 
if /i %op% == b (
    start notepad.exe
    goto:appwindows)
if /i %op% == t (
    start osk.exe
    goto:appwindows)
if /i %op% == p (
    start control.exe
    goto:appwindows)
if /i %op% == c (
    start calc.exe
    goto:appwindows)
if /i %op% == w (
    start explore.exe
    goto:appwindows)
if /i %op% == r (goto:menu) else (
	echo.
	echo Opção inválida!
	echo.
	pause
	goto:appwindows)

:servicos
cls
echo.
echo  ╔═════════════════════════════════════════════════╗
echo  ║ --------- SERVIÇOS DE REDE/DIVERSOS ----------- ║
echo  ║   [N] Navegar na Web                            ║
echo  ║   [G] Pesquisar conteúdo via Google             ║
echo  ║   [Y] Pesquisar conteúdo YouTube                ║
echo  ║   [T] Testar conexão de rede                    ║
echo  ║   [O] Obter IP da máquina                       ║
echo  ║   [R] Retornar ao menu                          ║
echo  ╚═════════════════════════════════════════════════╝
set /p op=Digite a opção desejada: 
if /i %op% == n (
	start chrome.exe
	goto:servicos)
if /i %op% == g (
    echo.
	set /p site=Digite o site a ser pesquisado: 
	start chrome.exe %site%
	goto:servicos)
if /i %op% == y (
    echo.
	set /p pesquisa=Digite o conteúdo a ser pesquisado: 
	start chrome.exe https://www.youtube.com/results?search_query=%pesquisa%
	goto:servicos)
if /i %op% == t (
    set /p conexao=Digite o IP da maquina ou endereco web: 
	ping %conexao% -t)
if /i %op% == o (
    ipconfig /all
	echo.
	echo.
	echo.
	pause
	goto:servicos)
if /i %op% == r (goto:menu) else (
	echo.
	echo Opção inválida! 
	echo.
	pause
	goto:servicos)

:jogos
cls
echo.
echo  ╔═════════════════════════════════════════════════╗
echo  ║ -------------------- JOGOS -------------------- ║
echo  ║    [A] Adivinhar o número                       ║
echo  ║    [J] Jo-kem-po                                ║
echo  ║    [R] Retornar ao menu                         ║
echo  ╚═════════════════════════════════════════════════╝

set /p op=Digite uma opção:
if /i %op% == a (goto:adivinhe)
if /i %op% == j (goto:jokempo)
if /i %op% == r (goto:menu) else (
	echo.
	echo Opção inválida! 
	echo.
	pause
	goto:jogos)
	
:adivinhe
cls
set /a vida=5
set /a numero=(%random% %%50) + 1
:continua
cls

	if %vida% == 0 (
		goto:resultado
	)
	
echo.
echo  ═══════════════ ADIVINHAR O NÚMERO ════════════════
echo     Adivinhe o número sorteado entre 1 e 50
echo     Qtde de vidas: %vida%
echo  ═══════════════════════════════════════════════════
set /p palpite=Digite seu palpite:
	
	if %palpite% lss 1 (
		echo.
		echo Número inválido! 
		echo.
		pause
		goto:continua
	)

	if %palpite% gtr 50 (
		echo.
		echo Número inválido! 
		echo.
		pause
		goto:continua
	)

	if %palpite% lss %numero% (
		echo.
		echo O número é maior!
		echo.
		set /a vida=%vida% -1
		pause
		goto:continua
	)

	if %palpite% gtr %numero% (
		echo.
		echo O número é menor! 
		echo.
		set /a vida=%vida% -1
		pause
		goto:continua
	)
	
	if %palpite% == %numero% (
		goto:resultado
	)
	
:resultado
cls
echo.
echo  ═══════════════ ADIVINHAR O NÚMERO ════════════════
echo     Adivinhe o número sorteado entre 1 e 50
echo     Qtde de vidas: %vida%
echo  ═══════════════════════════════════════════════════
echo.
if %vida% == 0 (
echo VOCÊ PERDEU! Suas vidas zeraram
echo O número era %numero%
) else (
	echo UHUUL PARABÉNS! Você acertou! 
	echo O número era %numero%)
echo.
set /p resp=Deseja jogar novamente [S/N]:
if /i %resp% == s (goto:adivinhe) else (goto:jogos)
	
:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

:jokempo
cls
set /a vitorias=0
set /a derrotas=0
set /a empates=0
echo.
echo  ════════════════════ JO-KEM-PO ════════════════════
echo     [J] JOGAR
echo     [R] REGRAS
echo     [V] VOLTAR À TELA DE JOGOS
echo  ═══════════════════════════════════════════════════
echo.
set /p op=Selecione uma opção:
if /i %op% == j (goto:nome)
if /i %op% == r (goto:regras)
if /i %op% == v (goto:jogos)

:nome
cls
echo.
set /p nome=Digite seu nome:

:jogarjkp
set /a comp=(%random% %%5) + 1
cls
echo.
echo  JOGADOR(A): %nome%
echo   [1] PEDRA
echo   [2] PAPEL
echo   [3] TESOURA
echo   [4] LAGARTO
echo   [5] SPOCK
echo   [S] SAIR
set /p op=Escolha a sua jogada:
echo.
if %op% == 1 (
	echo %nome% escolheu PEDRA
	goto:resultado)
if %op% == 2 (
	echo %nome% escolheu PAPEL
	goto:resultado)
if %op% == 3 (
	echo %nome% escolheu TESOURA
	goto:resultado)
if %op% == 4 (
	echo %nome% escolheu LAGARTO
	goto:resultado)
if %op% == 5 (
	echo %nome% escolheu SPOCK
	goto:resultado)
if /i %op% == s (goto:jokempo) else (
	echo.
	echo Opção inválida!
	echo.
	pause
	goto:jogarjkp)
	
:resultado
if %comp% == 1 (
	echo Computador escolheu PEDRA
	if %op% == 1 (
		echo EMPATE! 
		set /a empates=%empates% + 1)
	if %op% == 2 (
		echo VOCÊ GANHOU! 
		set /a vitorias=%vitorias% + 1)
	if %op% == 3 (
		echo VOCÊ PERDEU! 
		set /a derrotas=%derrotas% + 1)
	if %op% == 4 (
		echo VOCÊ PERDEU!
		set /a derrotas=%derrotas% + 1)
	if %op% == 5 (
		echo VOCÊ GANHOU! 
		set /a vitorias=%vitorias% + 1))
if %comp% == 2 (
	echo Computador escolheu PAPEL
	if %op% == 1 (
		echo VOCÊ PERDEU! 
		set /a derrotas=%derrotas% + 1)
	if %op% == 2 (
		echo EMPATE!
		set /a empates=%empates% + 1)
	if %op% == 3 (
		echo VOCÊ GANHOU! 
		set /a vitorias=%vitorias% + 1)
	if %op% == 4 (
		echo VOCÊ GANHOU! 
		set /a vitorias=%vitorias% + 1)
	if %op% == 5 (
		echo VOCÊ PERDEU! 
		set /a derrotas=%derrotas% + 1))
if %comp% == 3 (
	echo Computador escolheu TESOURA
	if %op% == 1 (
		echo VOCÊ GANHOU! 
		set /a vitorias=%vitorias% + 1)
	if %op% == 2 (
		echo VOCÊ PERDEU! 
		set /a derrotas=%derrotas% + 1)
	if %op% == 3 (
		echo EMPATE! 
		set /a empates=%empates% + 1)
	if %op% == 4 (
		echo VOCÊ PERDEU! 
		set /a derrotas=%derrotas% + 1)
	if %op% == 5 (
		echo VOCÊ GANHOU! 
		set /a vitorias=%vitorias% + 1))
if %comp% == 4 (
	echo Computador escolheu LAGARTO
	if %op% == 1 (
		echo VOCÊ GANHOU! 
		set /a vitorias=%vitorias% + 1)
	if %op% == 2 (
		echo VOCÊ PERDEU! 
		set /a derrotas=%derrotas% + 1)
	if %op% == 3 (
		echo VOCÊ GANHOU! 
		set /a vitorias=%vitorias% + 1)
	if %op% == 4 (
		echo EMPATE!
		set /a empates=%empates% + 1)
	if %op% == 5 (
		echo VOCÊ PERDEU! 
		set /a derrotas=%derrotas% + 1))
if %comp% == 5 (
	echo Computador escolheu SPOCK
	if %op% == 1 (
		echo VOCÊ PERDEU!
		set /a derrotas=%derrotas% + 1)
	if %op% == 2 (
		echo VOCÊ GANHOU! 
		set /a vitorias=%vitorias% + 1)
	if %op% == 3 (
		echo VOCÊ PERDEU! 
		set /a derrotas=%derrotas% + 1)
	if %op% == 4 (
		echo VOCÊ GANHOU! 
		set /a vitorias=%vitorias% + 1)
	if %op% == 5 (
		echo EMPATE! 
		set /a empates=%empates% + 1))
echo.
echo  ═════════════════════ PLACAR ══════════════════════
echo     = VITÓRIAS: %vitorias%
echo     = DERROTAS: %derrotas%
echo     = EMPATES: %empates%
echo  ═══════════════════════════════════════════════════
set /p resp=Deseja jogar novamente? [S/N]:
if /i %resp% == s (goto:jogarjkp) else (goto:jokempo)

:regras
cls
echo.
echo  ╔════════╦═════════╦═════════╦═════════╦═════════╦═════════╗
echo  ║        ║  PEDRA  ║  PAPEL  ║ TESOURA ║ LAGARTO ║  SPOCK  ║
echo  ╠════════╬═════════╬═════════╬═════════╬═════════╬═════════╣
echo  ║ EMPATE ║  pedra  ║  papel  ║ tesoura ║ lagarto ║  spock  ║
echo  ╠════════╬═════════╬═════════╬═════════╬═════════╬═════════╣
echo  ║ GANHA  ║ tesoura ║  pedra  ║ lagarto ║  papel  ║  pedra  ║
echo  ║        ║ lagarto ║  spock  ║  papel  ║  spock  ║ tesoura ║
echo  ╠════════╬═════════╬═════════╬═════════╬═════════╬═════════╣
echo  ║ PERDE  ║  papel  ║ tesoura ║  pedra  ║  pedra  ║ lagarto ║
echo  ║        ║  spock  ║ lagarto ║  spock  ║ tesoura ║  papel  ║
echo  ╚════════╩═════════╩═════════╩═════════╩═════════╩═════════╝
echo.
pause
goto:jokempo


:gerenciamento
cls
echo.
echo  ╔═════════════════════════════════════════════════╗
echo  ║ ---------- GERENCIAMENTO DA MÁQUINA ----------- ║
echo  ║   [D] Desligar a máquina                        ║
echo  ║   [I] Inicializar a máquina                     ║
echo  ║   [R] Retornar ao menu                          ║
echo  ╚═════════════════════════════════════════════════╝
set /p op=Digite a opção desejada: 
if /i %op% == d (goto:desligar)
if /i %op% == i (goto:inicializar)
if /i %op% == r (goto:menu) else (
	echo.
	echo Opção inválida! 
	echo.
	pause
	goto:gerenciamento)
	
:desligar
cls
echo.
echo  ═══════════════ DESLIGAR A MÁQUINA ═══════════════
set /p resp=Deseja mesmo desligar a máquina? [S/N]: 
if /i %resp% == s (shutdown -s
	pause
	goto:menu) else (goto:gerenciamento)

:inicializar
cls
echo.
echo  ═════════════ INICIALIZAR A MÁQUINA ══════════════
set /p resp=Deseja mesmo inicializar a máquina? [S/N]: 
if /i %resp% == s (shutdown -r
	pause
	goto:menu) else (goto:gerenciamento)

:encerrar
cls
echo.
echo  ═══════════════ ENCERRAR SESSÃO ══════════════════
set /p resp=Deseja mesmo encerrar sessão? [S/N]: 
if /i %resp% == s (goto:inicio) else (goto:menu)

:finalizar
cls
echo.
echo ══════════════ FINALIZAR PROGRAMA ════════════════
set /p resp=Deseja mesmo finalizar o programa? [S/N]: 
if /i %resp% == s (exit) else (goto:menu)