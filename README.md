# Project_ImmersionAlura_-IA4_SCIENCE

<h2 align="center">  IA4-SPACE (Artificial Intelligence for Space)
 </h2>

 

https://github.com/karenkessia/ProjectAlura_IA4_SCIENCE/assets/147193080/6a8f897f-f2c9-476d-8849-288e5042c106



 ### 🚀Introdução

 #### “Em um futuro não tão distante, interfaces com inteligência artificial (IA) podem ser usadas no espaço, permitindo interações entre astronautas e  veículos espaciais. A NASA demonstra estar se aventurando nesse mundo de chatbots e desenvolvimento com assistentes virtuais, o que é um salto na ciência. No ano passado, a pesquisadora e visitante da NASA Larissa Suzuki, contou que a agência espacial planeja usar uma versão inicial de uma interface com IA na futura estação espacial Lunar Gateway, cuja construção deve começar com a missão Artemis 4.
 #### Suzuki ressaltou que não é possível enviar engenheiros para investigar o porquê de uma nave espacial não estar se comunicando, ou quando um software apresenta problemas — é aqui que entra a IA.
#### No momento, os engenheiros da NASA estão trabalhando em uma interface própria, parecida com o chatbot Chat GPT. Quando estiver finalizada, ela pode permitir que astronautas conversem com suas naves, ou que os controladores das missões falem com robôs e suas IAs.”

#####  *referência bibliográfica - trecho retirado de* <https://www.terra.com.br/byte/ciencia/espaco/nasa-quer-usar-inteligencia-artificial-para-astronautas-e-naves-conversarem,0f0e9a54ac42f8c7599380e44914ffcektyi4282.html>

#### O mundo dos chatbots se apresenta como um universo empolgante e promissor, permeado por inteligência artificial e outras tecnologias. Diante desse cenário fascinante, desta descoberta científica, surge a oportunidade de desvendarmos os segredos da criação de chatbots, através de todo o aprendizado que obtivemos nas aulas sobre a criação deles, mesmo para aqueles que estão apenas dando seus primeiros passos nessa área. Através deste pequeno projeto, embarcaremos em uma breve jornada de aprendizado, explorando uma base conceitual lógica simplificada para o desenvolvimento de chatbots, mesmo para estudantes iniciantes. Utilizaremos as ferramentas: Linguagem Python, Gemini, Google AI STUDIO, Engenharia de Prompt.

#### *OBS: O código não se conecta a nenhum sistema real de controle de nave espacial ou ambiente espacial. É apenas uma simulação para fins de demonstração.*

### Funcionalidades

#### Este chatbot simula a comunicação entre astronautas e naves espaciais;

##### - Comunicação bidirecional: O usuário pode enviar mensagens para o chatbot e receber respostas.
##### - Obter informações: O(a) astronauta  pode consultar o chatbot para saber tais informações como:
##### - Status da nave: temperatura, localização.
##### - Andamento da missão: dados coletados até o momento.
##### - Controlar o ambiente: considerar ajustes.
##### - Temperatura: diminuir ou aumentar.
##### - Iluminação: ligar ou desligar.

### Assistência ao Astronauta

##### - Ajuda: O astronauta pode pedir ajuda ao chatbot a qualquer momento.
##### - Informação sobre a missão: O chatbot fornece detalhes sobre os objetivos e o progresso da missão.
##### - Interação em linguagem natural: O chatbot usa linguagem natural para se comunicar com o astronauta de forma amigável e intuitiva.

### Observações

##### - Simulação: Este projeto é uma simulação e não se conecta a nenhum sistema real de controle de nave espacial ou ambiente espacial.
##### - Funcionalidades básicas: O foco está nas funcionalidades básicas de comunicação e controle, mas funcionalidades mais complexas podem ser implementadas com bibliotecas adicionais.
##### - Linguagem de programação: O código Python demonstra a implementação das funcionalidades em um ambiente de texto, mas outras linguagens e interfaces podem ser utilizadas.

### Potencial para Aprimoramento

##### - Processamento de linguagem natural: O chatbot pode ser aprimorado para compreender frases mais complexas e responder de forma mais natural.
##### - Reconhecimento de voz: A interação pode ser mais intuitiva se o chatbot reconhecer a voz do astronauta.
##### - Controle de sistemas: O chatbot pode ser conectado a sistemas reais para controlar a temperatura, iluminação e outros aspectos do ambiente espacial.
##### - Interface gráfica: Uma interface gráfica pode tornar a interação com o chatbot mais amigável e visualmente atraente.

#### Seguindo a lógica em referência ao aprimoramento, irei adicionar um exemplo utilizando desta vez, a chave do Google AI Studio para reconhecimento de fala.

### Amostra com Recursos mais Avançados


```
import speech_recognition as sr
import gtts
from google.cloud import speech_v1p3 as speech
import os
import json

```
```
# Chave do Google AI Studio
CHAVE_GOOGLE_AI_STUDIO = "SEU_GOOGLE_AI_STUDIO_KEY"

# Função para reconhecer a fala do astronauta
def reconhecer_fala():
    r = sr.Recognizer()
    with sr.Microphone() as source:
        print("Fale agora:")
        audio = r.record(source)

    try:
        # Reconhecimento de fala usando Google AI Studio
        config = speech.RecognitionConfig(
            encoding=speech.RecognitionConfig.AudioEncoding.LINEAR16,
            language_code="pt-BR",
            sample_rate_hertz=44100,
            enable_automatic_punctuation=True,
        )
        audio_content = audio.get_raw_data()
        response = speech.recognize_audio(config=config, audio=audio_content)

        texto = response.results[0].alternatives[0].transcript
        print(f"Você disse: {texto}")
        return texto
    except sr.UnknownValueError:
        print("Não entendi o que você disse.")
    except sr.RequestError as e:
        print(f"Ocorreu um erro: {e}")

```
```
# Função para sintetizar a fala do chatbot
def sintetizar_fala(texto):
    tts = gtts.gTTS(text=texto, lang='pt-br')
    tts.save("resposta.mp3")
    print("Reproduzindo resposta...")
    os.system("mpg321 resposta.mp3")

```
```
# Função para processar o diálogo
def processar_dialogo(texto):
    # Utilizar PLN para entender o texto do astronauta
    # Acessar sistemas da nave espacial e obter informações relevantes
    # Gerar resposta para o astronauta

    resposta = "Ainda em desenvolvimento..."
    # Exemplo de processamento de diálogo:
    if texto.lower().startswith("status"):
        resposta = "Status da nave espacial:\n\n- Sistemas: Operando normalmente\n- Temperatura: 22°C\n- Pressão: 1013 hPa\n- Nível de oxigênio: 98%"

    return resposta

```
```
# Loop principal
while True:
    texto_astronauta = reconhecer_fala()
    resposta_chatbot = processar_dialogo(texto_astronauta)
    sintetizar_fala(resposta_chatbot)

```

### Explicação Detalhada do Exemplo

##### - Chave do Google AI Studio: A chave do Google AI Studio foi adicionada à função reconhecer_fala() para habilitar o reconhecimento de fala usando a API do Google AI Studio.
##### - Configuração de Reconhecimento: A configuração de reconhecimento foi definida para utilizar a codificação de áudio LINEAR16, a taxa de amostragem de 44100 Hz e a pontuação automática.
##### - Processamento de Resposta: A resposta da API do Google AI Studio é processada para extrair o texto reconhecido.

#####  *OBS: Substitua SEU_GOOGLE_AI_STUDIO_KEY pela sua chave real do Google AI Studio.*
##### - Certifique-se de que você ativou a API do Google Cloud Speech-to-Text em sua conta do Google Cloud Platform (GCP).
##### -  Você pode ajustar a configuração de reconhecimento de acordo com suas necessidades.

### Considerações

##### - A API do Google AI Studio pode ter limites de uso e latência mais altos do que a versão paga do Google Cloud Speech-to-Text.
##### - Para uso em produção
##### - Foi feita a prática de Engenharia de Prompt.

### Resumo Apresentado

##### Caso queira se aventurar ainda mais neste mundo de chatbots, seria muito interessante e importante obter demais recursos que trariam o máximo de realidade que desejamos. Ainda poderíamos brincar o suficiente com  hardware (portas, sockets e etc). Adicionar interfaces e enfim.









