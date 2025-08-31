# Alexa Skill - Modo Avançado (ChatGPT Integration)

Uma skill Alexa simples que integra com a API da OpenAI (ChatGPT) para responder perguntas através do comando de voz. 

**⚠️ Aviso Importante**: Esta skill foi desenvolvida como projeto pessoal e **não segue todas as melhores práticas** de desenvolvimento. No entanto, ela **está funcionando perfeitamente** e serve como uma excelente base para desenvolvedores aprenderem e implementarem suas próprias melhorias.

Ideal para desenvolvedores iniciantes que querem aprender como criar skills Alexa com integrações externas. Use este código como ponto de partida e evolua conforme suas necessidades!

## 🚀 Funcionalidades

- **Integração com OpenAI**: Usa GPT-4.1-mini para gerar respostas inteligentes
- **Interface Visual (APL)**: Exibe respostas em dispositivos Alexa com tela
- **Comando Simples**: Ative com "Alexa, abrir modo avançado" e pergunte qualquer coisa
- **Tratamento de Erros**: Gerenciamento robusto de erros da API
- **Suporte Português**: Skill configurada para português brasileiro

## 📋 Pré-requisitos

- **Conta Amazon Developer** (gratuita) - https://developer.amazon.com
- **Chave da API OpenAI** - https://platform.openai.com/api-keys
- **Conhecimento básico de JavaScript** e desenvolvimento web
- **Node.js versão 14 ou superior**
- **Dispositivos Alexa** (opcional, pode testar via simulador)

> **⚠️ IMPORTANTE**: Apenas clonar este repositório **NÃO** é suficiente! Você precisa criar e configurar a skill no Amazon Developer Console. Veja as instruções completas abaixo.

## 🛠️ Instalação e Configuração Completa

### Parte 1: Preparando o Código Localmente

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/seu-usuario/alexa-chatgpt-skill.git
   cd alexa-chatgpt-skill
   ```

2. **Instale as dependências:**
   ```bash
   npm install
   ```

3. **Configure sua chave da API OpenAI:**
   - Copie `keys.example.js` para `keys.js`
   - Substitua a chave pela sua chave real da OpenAI:
   ```javascript
   module.exports.OPEN_AI_KEY = 'sk-sua-chave-openai-aqui';
   ```

### Parte 2: Criando a Skill no Amazon Developer Console

> **Esta é a parte mais importante!** Sem isso, sua skill não funcionará.

> **⚠️ IMPORTANTE**: O "tutorial" abaixo **pode estar desatualizado**, dependendo de quais alterações foram feitas no processo e/ou frontend do Amazon Developer Console desde a criação dessa skill (que tem mais de 2 anos funcionando, antes da divulgação deste código publicamente aqui), então, verifique os procedimentos atualizados direto no portal, use IA's pra pedir ajuda e tirar dúvidas, enfim, você vai precisar estudar para implementar.

1. **Acesse o Amazon Developer Console:**
   - Vá para https://developer.amazon.com/alexa/console/ask
   - Faça login com sua conta Amazon (crie uma se não tiver)

2. **Crie uma nova Skill:**
   - Clique em "Create Skill" 
   - **Skill Name**: "Modo Avançado" (ou o nome que preferir)
   - **Primary Locale**: Portuguese (BR)
   - **Model**: Custom
   - **Hosting**: Alexa-hosted (Node.js) ou Provision your own
   - Clique "Create skill"

3. **Configure o Modelo de Interação:**
   - No painel esquerdo, vá em "Interaction Model" → "JSON Editor"
   - Apague todo o conteúdo
   - Copie e cole o conteúdo do arquivo `pt-BR.json` deste repositório
   - Clique "Save Model" e depois "Build Model"

4. **Configure o Endpoint:**

   **Opção A - AWS Lambda (Recomendado):**
   - Crie uma função Lambda no AWS Console
   - Faça upload do código (zip todos os arquivos)
   - Copie o ARN da função
   - No Developer Console: "Endpoint" → "AWS Lambda ARN" → Cole o ARN

   **Opção B - HTTPS Endpoint:**
   - Configure um servidor HTTPS próprio
   - No Developer Console: "Endpoint" → "HTTPS" → Cole a URL

### Parte 3: Configurando a Interface Visual (Opcional)

1. **No Developer Console, vá em "Interfaces"**
2. **Ative "Alexa Presentation Language (APL)"**
3. **Vá em "Multimodal Responses"**
4. **Adicione o documento APL:**
   - Copie o conteúdo de `resposta-visual.json`
   - Configure conforme necessário

### Parte 4: Teste e Publicação

1. **Testando em Desenvolvimento:**
   - No Developer Console, vá na aba "Test"
   - Mude de "Off" para "Development"
   - **Sua skill agora funciona em TODOS os seus dispositivos Alexa!**
   - Digite ou fale: "abrir modo avançado"

2. **Para Publicação (Opcional):**
   - Se quiser tornar a skill pública, vá na aba "Distribution"
   - Preencha todas as informações obrigatórias
   - **IMPORTANTE**: Leia a documentação completa da Amazon sobre o processo de certificação
   - Link: https://developer.amazon.com/docs/smapi/skill-submission-process.html

## 📁 Estrutura do Projeto

```
alexa-chatgpt-skill/
├── index.js                 # Handler principal da skill
├── keys.js                  # Configurações de API (não commitado)
├── package.json             # Dependências do projeto
├── pt-BR.json              # Modelo de interação em português
├── resposta-visual.json    # Template APL para interface visual
├── util.js                 # Utilitários AWS S3
├── local-debugger.js       # Debugger local (deprecated)
└── README.md               # Este arquivo
```

## 🎯 Como Usar

1. **Ativação da Skill:**
   ```
   "Alexa, abrir modo avançado"
   ```

2. **Fazendo Perguntas:**
   ```
   "Pergunta, qual o comando de Linux para desligar o PC?"
   "Pergunta, explique o que é inteligência artificial"
   "Pergunta, como fazer um bolo de chocolate?"
   ```

3. **Comandos de Controle:**
   - "Ajuda" - Mostra informações sobre a skill
   - "Parar" ou "Cancelar" - Encerra a sessão

## 🔧 Configuração Avançada

### Modificando o Modelo GPT

No arquivo `index.js`, você pode alterar o modelo usado na linha 59:
```javascript
model: "gpt-4.1-mini", // Altere para gpt-3.5-turbo, gpt-4, etc.
```

### Personalizando as Respostas

Modifique o prompt do sistema na linha 61-65 para personalizar o comportamento:
```javascript
{
    role: "system",
    content: "Você é uma assistente virtual de voz que responde perguntas de forma cordial. Data/Hora Atual: " + dataStr
}
```

### Interface Visual (APL)

O arquivo `resposta-visual.json` define como as respostas aparecem em dispositivos com tela. Você pode personalizar:
- Cores e tema
- Layout da resposta
- Imagens de fundo
- Logo da skill

## 📦 Deploy

### AWS Lambda (Recomendado para Iniciantes)

1. **Acesse o AWS Console** (https://aws.amazon.com)
2. **Procure por "Lambda" e clique em "Create Function"**
3. **Configure:**
   - Function name: `alexa-chatgpt-skill`
   - Runtime: Node.js 18.x
   - Permissions: Create a new role with basic Lambda permissions
4. **Faça upload do código:**
   - Compacte todos os arquivos (exceto `node_modules`) em um ZIP
   - No Lambda Console: "Upload from" → "Upload ZIP file"
   - Ou use: `npm run build && aws lambda update-function-code...`
5. **Configure variáveis de ambiente (opcional):**
   - Adicione `OPENAI_API_KEY` se quiser tirar do código
6. **Copie o Function ARN**
7. **No Developer Console da Alexa:** Endpoint → AWS Lambda ARN → Cole o ARN

### Servidor Próprio (Avançado)

1. Configure um servidor HTTPS (certificado SSL obrigatório)
2. Instale as dependências: `npm install`
3. Execute: `node index.js`
4. Configure o endpoint na skill com sua URL

> **💡 Dica**: Para desenvolvimento, use o Alexa-hosted (Node.js) no próprio Developer Console - é mais fácil para começar!

## 🐛 Troubleshooting

### "Skill não foi encontrada"
- Verifique se você está logado com a mesma conta Amazon no Developer Console e no dispositivo Alexa
- Confirme se a skill está com status "Development" ativado na aba Test
- Tente dizer o nome exato da skill: "Alexa, abrir modo avançado"

### Erro "Invalid API Key"
- Verifique se sua chave OpenAI está correta em `keys.js`
- Confirme se sua conta OpenAI tem créditos disponíveis
- Teste a chave diretamente na API da OpenAI

### "Skill não responde" ou "Houve um problema"
- Verifique se o endpoint está configurado corretamente no Developer Console
- Teste o modelo de interação no simulador do Developer Console
- Confira os logs do CloudWatch (se usando Lambda)
- Verifique se todas as dependências foram instaladas (`npm install`)

### Resposta truncada ou estranha
- A skill limita respostas a 1 parágrafo para melhor experiência de voz
- Modifique o prompt na linha 68 do `index.js` para respostas mais longas
- Verifique se não há problemas de encoding (caracteres especiais)

### Skill funciona no simulador mas não no dispositivo
- Aguarde alguns minutos - às vezes há delay para sincronizar
- Diga "Alexa, descobrir dispositivos" para forçar atualização
- Verifique se o dispositivo está na mesma conta Amazon

## 🤝 Contribuindo

Esta é uma skill educacional - contribuições são bem-vindas! Algumas ideias:

- [ ] Adicionar mais intents (intenções)
- [ ] Melhorar tratamento de erros
- [ ] Adicionar cache de respostas
- [ ] Implementar sessões persistentes
- [ ] Suporte a outros idiomas

## 📄 Licença

Este projeto é distribuído sob a licença Apache 2.0. Veja o arquivo `LICENSE` para mais detalhes.

## ⚠️ Importante

- **Custos**: Esta skill usa a API paga da OpenAI. Monitore seu uso para evitar custos inesperados
- **Rate Limits**: A OpenAI tem limites de requisições. Implemente cache se necessário
- **Segurança**: Nunca commite suas chaves de API. Use variáveis de ambiente em produção

## 📞 Suporte

- Abra uma issue neste repositório para bugs
- Para dúvidas sobre desenvolvimento Alexa: [Amazon Developer Forums](https://forums.developer.amazon.com/)
- Para problemas com OpenAI: [OpenAI Support](https://help.openai.com/)

## 🎓 Para Desenvolvedores Iniciantes

Esta skill é um ótimo ponto de partida para aprender:

1. **Estrutura básica de uma Alexa Skill**
2. **Integração com APIs externas (OpenAI)**
3. **Tratamento de erros em Node.js**
4. **Uso de interfaces visuais (APL)**
5. **Deploy em AWS Lambda**
6. **Configuração no Amazon Developer Console**

### 📚 Recursos de Aprendizado Complementares

- **Documentação Oficial Alexa**: https://developer.amazon.com/docs/ask-overviews/build-skills-with-the-alexa-skills-kit.html
- **Curso Gratuito Amazon**: https://developer.amazon.com/en-US/alexa/alexa-skills-kit/training
- **OpenAI API Docs**: https://platform.openai.com/docs
- **Node.js para Iniciantes**: https://nodejs.org/en/learn

### 🚀 Próximos Passos Sugeridos

1. **Comece simples**: Faça a skill funcionar exatamente como está
2. **Experimente**: Mude as mensagens, teste diferentes prompts
3. **Melhore gradualmente**: Adicione validações, logs, tratamento de erro
4. **Expanda**: Adicione novos intents, funcionalidades
5. **Otimize**: Implemente cache, rate limiting, monitoramento

### ⚠️ Pontos de Melhoria (para você implementar!)

- [ ] Validação mais robusta de inputs
- [ ] Sistema de logs estruturado
- [ ] Cache de respostas para reduzir custos
- [ ] Rate limiting para evitar abuso
- [ ] Testes automatizados
- [ ] Configuração via variáveis de ambiente
- [ ] Documentação do código
- [ ] Monitoramento e métricas

Estude o código, experimente e não tenha medo de quebrar coisas! É assim que se aprende! 🚀

---

**Nota**: Esta skill foi criada para fins educacionais. Use como base para seus próprios projetos!
