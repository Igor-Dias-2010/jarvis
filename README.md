# Jarvis

Assistente pessoal por voz para PC, inspirado no Jarvis do Tony Stark. Ele reconhece seu rosto, entende o que você fala em português, responde com uma voz grave e séria, executa tarefas no computador e mostra tudo em uma interface animada.

Este repositório é o **ponto de entrada**. Ele não tem o código dos serviços: aqui você encontra o guia de como tudo se encaixa e os links de cada repositório.

## O que o Jarvis faz

- Aparece quando você chama ("Jarvis")
- Reconhece que é você pelo rosto antes de liberar ações sensíveis
- Entende sua voz (português) e responde falando
- Interface com um círculo animado que reage à sua voz e à voz dele
- Automatiza tarefas: abrir programas, arquivos, volume, janelas
- Integra com email e WhatsApp

## Como funciona

Cada função é um serviço independente, em um repositório próprio. Os serviços conversam entre si por mensagens (WebSocket) usando os formatos definidos em `jarvis-contracts`.

```
Você fala -> voice-in -> core (LLM + ferramentas) -> voice-out -> Você ouve
                          |-> pc (automação)
                          |-> integrations (email, WhatsApp)
              vision -> core (quem está na frente da câmera)
              ui <- core (estado: ouvindo, pensando, falando)
```

## Repositórios

| Serviço | Função | Link |
|---|---|---|
| `jarvis-contracts` | Formato das mensagens entre os serviços | em breve |
| `jarvis-core` | Cérebro: LLM, ferramentas e orquestração | em breve |
| `jarvis-voice-out` | Voz do Jarvis (TTS) | em breve |
| `jarvis-voice-in` | Palavra de ativação e reconhecimento de voz | em breve |
| `jarvis-ui` | Interface animada | em breve |
| `jarvis-vision` | Reconhecimento facial | em breve |
| `jarvis-pc` | Controle do computador | em breve |
| `jarvis-integrations` | Email | em breve |

Ordem recomendada de construção: contracts, core, voice-out, voice-in, ui, vision, pc, integrations.

## Como usar (passo a passo)

1. **Requisitos:** Python 3.11+, Node.js 20+ (para a interface), Git, webcam e microfone.
2. **Clone o projeto com os serviços:**
   ```bash
   git clone --recurse-submodules https://github.com/SEU-USUARIO/jarvis.git
   cd jarvis
   ```
3. **Instale cada serviço** seguindo o README dentro da pasta dele.
4. **Configure** as chaves e permissões em um arquivo `.env` (cada serviço explica o que precisa).
5. **Cadastre seu rosto** pelo serviço `vision`.
6. **Inicie** os serviços e chame: "Jarvis".

> Os passos 3 a 6 passam a valer conforme os repositórios forem publicados.

## Segurança

- O Jarvis só executa ações de uma lista permitida.
- Ações destrutivas (apagar, instalar, enviar mensagem) pedem confirmação por voz.
- O reconhecimento facial não é a única proteção: use também a verificação de que a pessoa é real (piscar, mover a cabeça).
- Nunca envie seu `.env` para o GitHub.
- WhatsApp: não existe API oficial para conta pessoal. Bibliotecas não oficiais podem causar banimento do número. Use por sua conta e risco.

## Status

- [ ] contracts
- [ ] core
- [ ] voice-out
- [ ] voice-in
- [ ] ui
- [ ] vision
- [ ] pc
- [ ] integrations