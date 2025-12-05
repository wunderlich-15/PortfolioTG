# 1º Semestre - 2022/1

## Mó viagem
Repositório:<a href="https://github.com/lucasetdasilva/GrupoCachinhos">GIT</a>

Projeto do primeiro semestre tinha como cliente a própria Faculdade de tecnologia de São José dos Campos, se trata de um assistente virtual de viagens, serve para auxiliar o usuário a planejar futuras viagens tendo como funcionalidades:
- `Previsão do tempo`: Nesta função, o usuário pode pesquisar a previsão do tempo no destino desejado. </br>
- `Lista de desejos`: Através desta funcionalidade, o usuário pode criar uma lista de locais que ele deseja visitar.</br>
- `Avaliações no app`: O usuário poderá falar para outros usuários suas experiências de viagens e recomendações de lugares.</br>
- `Pesquisa de agências`: Função a qual será mostrado agências e suas respectivas categorias (Ecoturismo, Gastronomia, Para toda Família e Parques Temáticos).</br>
- `Roteiro de viagens`: De acordo com a cidade, será mostrado ao usuário pontos turísticos.</br>
- `Comparação de preços`: O programa redirecionará o usuário para outro site onde ele poderá comparar os preços das passagens aéreas.</br>
- `Curiosidades`: Serve caso o usuário queira saber um pouco mais sobre uma cidade.</br>
- `Calendário de Feriados`: Será feito um calendário que mostrará os próximos feriados prolonagados.</br>
- `Locais mais procurados por estação do ano`: É mostrado ao usuário os melhores destinos por estação do ano.</br>

## Tecnologias
Foi utilizado como única linguagem de programação o Python no backend e suas bibliotecas especificas voltadas ao projeto, o sistema funciona 100% pelo console e com reconhecimento de voz algumas das bibiliotecas utilizadas foram:
- **SpeechRecognition**: Utilizada para o reconhecimento de voz e comandos.
- **PyAudio**: Interface Python para trabalhar com áudio.
- **API OpenWeather**: API de clima em python, utilizada para a rpevisão do tempo.
- **Pandas**: Analisa e manipula os dados obtidos no código.
- **Wikipédia**: Realiza pesquisas retornando dados diretamtne da Wikipédia.
- **Requests**: Simplifica requisições HTTP.
- **Translator**: bibilioteca para tradução em python.
- **Holidays**: Informa sobre feriados em diversos países.
- **Webbrowser**: Abre URLs no navegador padrão do dispositivo onde o sistema está em uso.
- **Pyttsx3**: Síntese de voz no Python.

## Contribuições Pessoais

### Previsão do tempo e Calendário de Feriados: 
Como desenvolvedor implementei com a Tecnologia do Python,  utilizando as bibliotecas da API OpenWeather, PyAudio, Holidays e Webbrowser. Fiz uso dessas bibliotecas trabalhando em conjunto para que assim conseguisse retornar ao usuario funções indispensáveis para o planejamento de uma viagem como o calendário de feriados do destino e a previsão do clima que estaria no local pretendido, podendo retornar até o mês inteiro de planejamento possível para o usuário.
Exemplos dos Códigos Abaixo:

#### Previsão do tempo:

<details>
<summary><h4>Mais Detalhes</h4></summary>
   
``` python
   #Previsão do tempo
        if "previsão do tempo" in texto:
            convertFala("Para onde você pretende ir")
            api = "a143cba82f2ee6901732e51ece9014df"
            rec = sr.Recognizer()
            
            with sr.Microphone() as mic:
                print("ouvindo")
                rec.adjust_for_ambient_noise(mic)
                audio = rec.listen(mic)
            
            cidade = rec.recognize_google(audio, language="pt-BR")
            
            url = f"https://api.openweathermap.org/data/2.5/weather?q={cidade}&appid={api}"
            req = requests.get(url)
            requisicao_dic = req.json()
            tempo = requisicao_dic['weather'][0]['description']
            temperatura = requisicao_dic['main']['temp']
            converter = (temperatura - 273.15) // 1
            clima = tradutor(tempo)
            convertFala(f"Em {cidade} faz agora {converter} graus Celsius")
            convertFala(f"A condição climática é {clima}")
            print(f"Temperatura agora em {cidade} é {converter} °C")
            print(f"Condição climática agora em {cidade} é {clima}")

            if (converter >= 28):
                convertFala("Passe um filtro solar e beba bastante água, hoje será um dia quente")

            elif (converter <= 15):
                convertFala("Melhor se agasalhar, hoje o dia vai estar frio")

            elif (converter >= 16 and converter <= 27):
                convertFala("Hoje o clima estará agradável, aproveite")
```

</details>

### Calendário de Feriados

<details>
<summary><h4>Mais Detalhes</h4></summary>

``` python
#Calendario de Feriados
        elif "calendário" or "calendário de feriados" in texto:
            
          convertFala("Fale o mês que deseja saber os feriados")
          print("")
          mf = sr.Recognizer()
          with sr.Microphone() as mic:
                print("Qual o mês")
                mf.adjust_for_ambient_noise(mic)
                audio = mf.listen(mic)
                
          mes = mf.recognize_google(audio, language="pt-BR")

          if "janeiro" in mes:
              for feriado in feriados['2022-01-01': '2022-01-31'] :
                convertFala('As datas com feriado em Janeiro são: \n')

                x = str(feriado)
                x = re.sub("datetime.date",'',x)
                x = re.sub('{','',x)
                x = re.sub('}','',x)
                print(x)
                convertFala(x)

          elif "fevereiro" in mes:
              for feriado in feriados['2022-02-01': '2022-02-28'] :
                convertFala('As datas com feriado em Fevereiro são: \n')

                x = str(feriado)
                x = re.sub("datetime.date",'',x)
                x = re.sub('{','',x)
                x = re.sub('}','',x)
                print(x)
                convertFala(x)

          elif "março" in mes:
              for feriado in feriados['2022-03-01': '2022-03-31'] :
                convertFala('As datas com feriado em Março são: \n')

                x = str(feriado)
                x = re.sub("datetime.date",'',x)
                x = re.sub('{','',x)
                x = re.sub('}','',x)
                print(x)
                convertFala(x)

          elif "abril" in mes:
              for feriado in feriados['2022-04-01': '2022-04-30'] :
                convertFala('As datas com feriado em Abril são: \n')

                x = str(feriado)
                x = re.sub("datetime.date",'',x)
                x = re.sub('{','',x)
                x = re.sub('}','',x)
                print(x)
                convertFala(x)
                
                
          elif "maio" in mes:
              for feriado in feriados['2022-05-01': '2022-05-30'] :
                convertFala('As datas com feriado em Maio são: \n')

                x = str(feriado)
                x = re.sub("datetime.date",'',x)
                x = re.sub('{','',x)
                x = re.sub('}','',x)
                print(x)
                convertFala(x)

          elif "junho" in mes:
              for feriado in feriados['2022-06-01': '2022-06-31'] :
                convertFala('As datas com feriado em Junho são: \n')

                x = str(feriado)
                x = re.sub("datetime.date",'',x)
                x = re.sub('{','',x)
                x = re.sub('}','',x)
                print(x)
                convertFala(x)

          elif "julho" in mes:
              for feriado in feriados['2022-07-01': '2022-07-30'] :
                convertFala('As datas com feriado em Julho são: \n')

                x = str(feriado)
                x = re.sub("datetime.date",'',x)
                x = re.sub('{','',x)
                x = re.sub('}','',x)
                print(x)
                convertFala(x)

          elif "agosto" in mes:
              for feriado in feriados['2022-08-01': '2022-08-31'] :
                convertFala('As datas com feriado em Agosto são: \n')

                x = str(feriado)
                x = re.sub("datetime.date",'',x)
                x = re.sub('{','',x)
                x = re.sub('}','',x)
                print(x)
                convertFala(x)

          elif "setembro" in mes:
              for feriado in feriados['2022-09-01': '2022-09-30'] :
                convertFala('As datas com feriado em Setembro são: \n')

                x = str(feriado)
                x = re.sub("datetime.date",'',x)
                x = re.sub('{','',x)
                x = re.sub('}','',x)
                print(x)
                convertFala(x)

          elif "outubro" in mes:
              for feriado in feriados['2022-10-01': '2022-10-31'] :
                convertFala('As datas com feriado em Outubro são: \n')

                x = str(feriado)
                x = re.sub("datetime.date",'',x)
                x = re.sub('{','',x)
                x = re.sub('}','',x)
                print(x)
                convertFala(x)

          elif "novembro" in mes:
              for feriado in feriados['2022-11-01': '2022-11-30'] :
                convertFala('As datas com feriado em Novembro são: \n')

                x = str(feriado)
                x = re.sub("datetime.date",'',x)
                x = re.sub('{','',x)
                x = re.sub('}','',x)
                print(x)
                convertFala(x)

          elif "dezembro" on mes:
              for feriado in feriados['2022-12-01': '2022-12-31'] :
                convertFala('As datas com feriado em Dezembro são: \n')

                x = str(feriado)
                x = re.sub("datetime.date",'',x)
                x = re.sub('{','',x)
                x = re.sub('}','',x)
                print(x)
                convertFala(x)

```
</details>

### Lições aprendidas
Foi o primeiro contato com um projeto integrador e pude desenvolver minhas habilidades como trabalho em equipe, comunicação e lidar com prazos e pedidos do cliente, pude trabalhar meu raciocinio lógico e aprendi novas formas de sair de situações com as quais achei que ja sabia como lidar.

#### Hard Skills

<details>
   
| Habilidade | Nota | Classificação |
| :-----: | :-----: | :-----: | 
| Python | ★★★☆☆ | Sei fazer com ajuda|
| Lógica de programação | ★★★☆☆ | Sei fazer com ajuda |
| SCRUM |	★★★★☆ | Entendi |

</details>

#### Soft Skills
<details>

| Habilidade | Classificação |
| :-----: | :-----: |
| Trabalho em equipe | Colaborei de forma eficiente com o grupo, ouvindo atentamente, compartilhando ideias e mantendo empatia, sempre com foco no objetivo final do projeto e no sucesso coletivo. |
| Comunicação | Utilizei a comunicação constante ao longo do projeto para organizar o backlog, definir tarefas e garantir que as atualizações e feedbacks fossem compartilhados de maneira clara e eficiente. |
| Proatividade	| Tive uma maior noção do significado correto de proatividade onde aprendi a como me portar corretamente num modelo de projeto orientado a metodologia ágil Scrum e como cada task impacta no desenvolvimento. |

</details>


[Página Inicial](https://github.com/wunderlich-15/PortfolioTG/tree/main)
