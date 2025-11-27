# 🚀 ETL com IA Generativa (Google Gemini)

Projeto desenvolvido inspirado no **Santander Dev Week 2023**, explorando o conceito de ETL (Extract, Transform, Load) integrado à Inteligência Artificial do Google.

## 📋 Descrição
O objetivo deste projeto é criar um pipeline de dados que:
1.  **Extrai** dados de funcionários de um arquivo CSV (simulando um sistema legado).
2.  **Transforma** esses dados utilizando a API do **Google Gemini (modelo 2.0 Flash)** para gerar feedbacks personalizados de avaliação de desempenho.
3.  **Carrega** os dados enriquecidos de volta para um novo arquivo CSV pronto para envio.

## 🛠️ Tecnologias Utilizadas
* **Python 3**
* **Pandas** (Manipulação de dados)
* **Google Generative AI** (Integração com LLM Gemini)

## ⚙️ Como Utilizar
1.  Clone este repositório.
2.  Instale as dependências:
    ```bash
    pip install pandas google-generativeai
    ```
3.  Gere sua API Key no [Google AI Studio](https://aistudio.google.com/).
4.  Insira sua chave no código onde diz `"SUA_CHAVE_AQUI"`.
5.  Execute o script/notebook.

## 📊 Exemplo de Resultado
| Nome | Cargo | Nota | Feedback Gerado pela IA |
|------|-------|------|-------------------------|
| Ana | Dev | 9.5 | "Ana, seu desempenho excepcional demonstra expertise..." |
| Beatriz | Designer | 5.5 | "Beatriz, seu desempenho demonstra potencial, mas podemos trabalhar juntos..." |

---
*Projeto desenvolvido para fins de estudo em Engenharia de Dados e IA.*

### 🔍 Utilitário: Listando Modelos Disponíveis

Como a API do Google Gemini é atualizada frequentemente com novas versões (ex: `gemini-1.5-flash`, `gemini-2.0`), incluí um script para listar exatamente quais modelos estão disponíveis para a sua API Key.

**Código de Verificação:**

```python
import google.generativeai as genai

GOOGLE_API_KEY = "SUA_CHAVE_AQUI"
genai.configure(api_key=GOOGLE_API_KEY, transport='rest')

# Lista todos os modelos que suportam geração de conteúdo
for m in genai.list_models():
    if 'generateContent' in m.supported_generation_methods:
        print(f"- {m.name}")