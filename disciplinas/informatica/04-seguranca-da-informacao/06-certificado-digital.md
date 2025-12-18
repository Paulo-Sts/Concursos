# Certificado Digital

## 1. Conceito de Certificado Digital
- É um registro eletrônico que funciona como uma identidade digital para pessoas físicas (e-CPF), jurídicas (e-CNPJ), equipamentos ou serviços.
- Sua principal função é associar uma pessoa ou entidade a uma chave pública.
- Funciona como um "passaporte virtual" que atesta a identidade do titular em ambiente eletrônico.

## 2. ICP-Brasil (Infraestrutura de Chaves Públicas Brasileira)
- É a cadeia hierárquica que viabiliza a emissão de certificados digitais no Brasil.
- Garante a validade jurídica de documentos eletrônicos, equivalente à assinatura de próprio punho com firma reconhecida.
- Proporciona segurança para transações online, garantindo autenticidade, integridade e não repúdio.

## 3. Funcionamento e Garantias
- O certificado digital é utilizado para gerar a assinatura digital.
- Garante três pilares fundamentais:
  - Autenticidade: Certeza de quem emitiu o documento.
  - Integridade: Garantia de que o documento não foi alterado.
  - Não Repúdio: O autor não pode negar a autoria da assinatura.
- Opcionalmente, pode garantir a Confidencialidade (através do sigilo dos dados).

## 4. Agentes da ICP-Brasil
- AC (Autoridade Certificadora): Entidade responsável por emitir, distribuir, renovar e revogar os certificados. É como o "cartório" digital.
- AR (Autoridade de Registro): Interface entre o usuário e a AC. Identifica o usuário e encaminha os pedidos de certificado.
- ACT (Autoridade de Carimbo de Tempo): Responsável por atestar a data e hora exatas em que um documento foi assinado.

## 5. Diferenças Importantes
- Assinatura Digital: O ato de assinar o documento usando a chave privada do certificado.
- Certificado Digital: O documento eletrônico que contém a chave pública e os dados do titular.
- Hash: Função que garante a integridade (se o arquivo mudou, o hash muda), mas sozinha não garante a autoria.

## 6. Pontos-Chave para Concursos
- Chave Pública: O certificado digital associa uma entidade a uma chave pública (questão recorrente).
- Validade Jurídica: Documentos assinados via ICP-Brasil possuem presunção de veracidade.
- Auditoria: Através dos Logs (registros de eventos), é possível auditar o acesso e verificar falhas de segurança.
- IDS/IPS: O IDS monitora o tráfego passivamente, enquanto o IPS pode agir para bloquear invasões em tempo real.