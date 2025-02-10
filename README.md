# Projeto de Configuração de Pesquisa com IA

Este projeto foi desenvolvido como parte do curso "Microsoft Certified: Azure AI Fundamentals". Abaixo estão os passos seguidos para configurar uma pesquisa com IA, insights obtidos, possibilidades de ferramentas que se beneficiam dessa tecnologia e aprendizados adquiridos durante o processo.

## Passo a Passo para Configurar uma Pesquisa com IA

1. **Configuração do Ambiente**
   - Crie uma conta no Azure.
   - Configure um novo recurso de Pesquisa Cognitiva no portal do Azure.
   - Instale o SDK do Azure Cognitive Search:
     ```bash
     pip install azure-search-documents
     ```

2. **Criação do Índice de Pesquisa**
   - Defina o esquema do índice, incluindo campos e tipos de dados.
   - Crie o índice no serviço de Pesquisa Cognitiva:
     ```python
     from azure.search.documents import SearchClient
     from azure.search.documents.indexes import SearchIndexClient
     from azure.search.documents.indexes.models import SearchIndex, SimpleField, SearchFieldDataType

     index_client = SearchIndexClient(endpoint="your-endpoint", credential="your-credential")

     fields = [
         SimpleField(name="id", type=SearchFieldDataType.String, key=True),
         SimpleField(name="content", type=SearchFieldDataType.String)
     ]

     index = SearchIndex(name="my-index", fields=fields)
     index_client.create_index(index)
     ```

3. **Carregamento de Dados**
   - Prepare os dados para serem indexados.
   - Carregue os dados no índice de pesquisa:
     ```python
     from azure.search.documents import SearchClient

     search_client = SearchClient(endpoint="your-endpoint", index_name="my-index", credential="your-credential")

     documents = [
         {"id": "1", "content": "A inteligência artificial está transformando o mundo."},
         {"id": "2", "content": "O aprendizado de máquina é uma subárea da IA."}
     ]

     search_client.upload_documents(documents=documents)
     ```

4. **Realização de Pesquisas**
   - Execute consultas de pesquisa no índice criado:
     ```python
     results = search_client.search(query="inteligência artificial")
     for result in results:
         print(result)
     ```

## Insights e Possibilidades

- **Insights**:
  - A configuração de um serviço de pesquisa com IA permite a criação de sistemas de busca eficientes e precisos.
  - A flexibilidade na definição do esquema do índice facilita a adaptação a diferentes tipos de dados e necessidades de pesquisa.

- **Possibilidades de Ferramentas**:
  - **Sistemas de Busca Interna**: Empresas podem implementar sistemas de busca interna para facilitar o acesso a documentos e informações.
  - **Motores de Busca Personalizados**: Plataformas online podem criar motores de busca personalizados para melhorar a experiência do usuário.
  - **Análise de Dados**: Ferramentas de análise de dados podem se beneficiar da capacidade de pesquisa para encontrar padrões e insights rapidamente.

## Aprendizados Adquiridos

- **Configuração e Uso do Azure Cognitive Search**: Aprendi a configurar e utilizar o serviço de Pesquisa Cognitiva do Azure, desde a criação do índice até a execução de consultas.
- **Importância da Estruturação de Dados**: A estruturação adequada dos dados é crucial para a eficácia das pesquisas.
- **Aplicações Práticas da Pesquisa com IA**: Entendi como a pesquisa com IA pode ser aplicada em diversos cenários para melhorar a eficiência e a precisão na recuperação de informações.

## Conclusão

Este projeto demonstra a configuração e utilização de um serviço de pesquisa com IA utilizando o Azure Cognitive Search. Os insights e aprendizados adquiridos mostram a importância e as possibilidades dessa tecnologia em diferentes contextos.
