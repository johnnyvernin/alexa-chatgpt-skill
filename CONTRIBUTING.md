# Contribuindo para a Alexa Skill ChatGPT

Obrigado pelo interesse em contribuir! Esta skill foi criada com propósito educacional e toda ajuda é bem-vinda.

## 🤝 Como Contribuir

### Reportando Bugs

1. Verifique se o bug já não foi reportado nas [Issues](https://github.com/johnnyvernin/alexa-chatgpt-skill/issues)
2. Abra uma nova issue com:
   - Descrição clara do problema
   - Passos para reproduzir
   - Comportamento esperado vs atual
   - Screenshots se aplicável
   - Informações do ambiente (Node.js version, etc.)

### Sugerindo Melhorias

1. Abra uma issue com tag `enhancement`
2. Descreva a melhoria proposta
3. Explique por que seria útil
4. Se possível, sugira como implementar

### Contribuindo com Código

1. **Fork** o repositório
2. **Clone** seu fork localmente:
   ```bash
   git clone https://github.com/seu-usuario/alexa-chatgpt-skill.git
   ```
3. **Crie** uma branch para sua feature:
   ```bash
   git checkout -b feature/minha-nova-feature
   ```
4. **Faça** suas alterações
5. **Teste** localmente
6. **Commit** suas mudanças:
   ```bash
   git commit -m "feat: adiciona nova funcionalidade X"
   ```
7. **Push** para sua branch:
   ```bash
   git push origin feature/minha-nova-feature
   ```
8. **Abra** um Pull Request

## 📝 Padrões de Código

### JavaScript
- Use ES6+ quando possível
- Mantenha funções pequenas e focadas
- Comente código complexo
- Use nomes descritivos para variáveis

### Commits
Use conventional commits:
- `feat:` para novas funcionalidades
- `fix:` para correções
- `docs:` para documentação
- `refactor:` para refatoração
- `test:` para testes

### Estrutura de Arquivos
- Mantenha a estrutura atual
- Novos handlers vão em `index.js`
- Utilitários em `util.js`
- Configurações em arquivos separados

## 🧪 Testando

Antes de submeter seu PR:

1. **Teste localmente:**
   ```bash
   npm install
   # Configure suas keys
   node index.js
   ```

2. **Teste na Alexa Developer Console**
3. **Verifique se não quebrou funcionalidades existentes**

## 💡 Ideias de Contribuição

### Para Iniciantes
- [ ] Melhorar mensagens de erro
- [ ] Adicionar mais exemplos de uso
- [ ] Traduzir comentários para inglês
- [ ] Melhorar documentação

### Funcionalidades Intermediárias
- [ ] Adicionar cache de respostas
- [ ] Implementar rate limiting
- [ ] Adicionar logs estruturados
- [ ] Suporte a múltiplos modelos OpenAI

### Funcionalidades Avançadas
- [ ] Persistência de sessões
- [ ] Integração com outros LLMs
- [ ] Métricas e monitoramento
- [ ] Suporte multi-idioma

## 🚫 O que NÃO aceitar

- Código que quebra compatibilidade sem justificativa
- Mudanças que comprometem a segurança
- Features muito específicas que não agregam para maioria
- Código sem documentação adequada

## 📞 Dúvidas

- Abra uma issue com tag `question`
- Entre em contato via email (se disponível)
- Participe das discussões existentes

## 📄 Licença

Ao contribuir, você concorda que suas contribuições serão licenciadas sob a mesma licença Apache 2.0 do projeto.

---

**Lembre-se**: Esta é uma skill educacional! O objetivo é ajudar desenvolvedores iniciantes a aprender. Mantenha o código simples e bem documentado. 🎓
