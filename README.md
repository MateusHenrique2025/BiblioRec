# 📚 BiblioRec — Sistema de Recomendação de Livros Técnicos - Modelo Inicial

> Protótipo funcional de uma **biblioteca acadêmica inteligente** que recomenda livros técnicos com base no **curso** do aluno e no seu **histórico de empréstimos**.

Projeto desenvolvido como **estudo de caso** para aplicação prática das **5 partes da norma ISO/IEC/IEEE 29119** (Testes de Software).

---

## 🎯 Sobre o projeto

O **BiblioRec** simula uma biblioteca universitária moderna com **Machine Learning** para sugerir livros relevantes a cada aluno. Possui duas interfaces web:

- 👨‍🎓 **Área do Aluno** — login, cadastro, recomendações, empréstimo e devolução
- 🔐 **Painel do Admin** — dashboard completo de gestão do acervo

> 🤖 **Nota:** este projeto foi desenvolvido com o auxílio de **Inteligência Artificial - deepseek** (assistente de código), que contribuiu para a estruturação do motor de recomendação, das interfaces Gradio, do banco de dados SQLite e da documentação. O código foi revisado, adaptado e testado para atender aos requisitos acadêmicos da disciplina.

---

## ✨ Funcionalidades

### 👨‍🎓 Área do Aluno
- 🔐 Login e cadastro (SHA-256)
- 🎯 Recomendações personalizadas (motor híbrido)
- 📥 Empréstimo de livros
- 🔄 Devolução com atualização de estoque
- 📖 Histórico de empréstimos

### 🔐 Painel do Administrador
- 📈 Resumo geral (alunos, livros, empréstimos)
- 👥 Usuários cadastrados
- 📚 Estoque de livros
- 📕 Empréstimos ativos (quem está com o quê)
- 📗 Histórico de devoluções
- 📋 Histórico completo
- 🔍 Consulta cruzada aluno ↔ livro
- ➕ Cadastro de novos livros

---

## 🧠 Motor de recomendação

Abordagem **híbrida** que combina duas técnicas:

| Técnica | Peso | Como funciona |
|---------|:---:|---------------|
| **Filtragem por Conteúdo** | 60% | **TF-IDF** + **Similaridade de Cosseno** entre o perfil do curso e o perfil dos livros |
| **Filtragem Colaborativa** | 40% | **KNN** com cosseno sobre matriz `aluno × livro` do histórico de empréstimos |

```python
score_final = 0.6 * score_conteudo + 0.4 * score_colaborativo
