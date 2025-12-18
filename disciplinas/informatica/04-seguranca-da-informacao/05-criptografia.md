# Criptografia

## 1. Conceito de Criptografia
- É a ciência e a arte de escrever mensagens em forma cifrada ou em código.
- Principal mecanismo de segurança para proteção de dados na Internet.
- Objetivos principais: Confidencialidade, Integridade, Autenticidade e Não Repúdio.

## 2. Tipos de Criptografia (Quanto às Chaves)

#### Criptografia de Chave Simétrica
- Também chamada de chave única, secreta ou compartilhada.
- Utiliza a mesma chave tanto para codificar (cifrar) quanto para decodificar (decifrar).
- Foco principal: Garantir a confidencialidade dos dados.

#### Criptografia de Chave Assimétrica
- Utiliza um par de chaves distintas: uma Chave Pública e uma Chave Privada.
- Chave Pública: Pode ser divulgada livremente para qualquer pessoa.
- Chave Privada: Deve ser mantida em segredo absoluto pelo dono.
- Funcionamento: O que uma chave codifica, apenas a outra do mesmo par pode decodificar.
- Objetivos: Além da confidencialidade, garante autenticidade, integridade e o não repúdio.

## 3. Assinatura Digital e Hash

#### Assinatura Digital
- Utiliza criptografia assimétrica (chave privada do remetente) para garantir que uma mensagem ou documento é autêntico.
- Garante: Autenticidade, Integridade e Não Repúdio (o autor não pode negar que assinou).

#### Função Resumo (Hash)
- É um método que, aplicado sobre qualquer informação, gera um resultado único de tamanho fixo.
- Características: Funciona como uma "impressão digital" do arquivo. Se um único bit for alterado no arquivo original, o código Hash muda completamente.
- Objetivo: Garantir a Integridade dos dados.

## 4. Termos e Conceitos Adicionais
- Criptografia de César: Método antigo onde cada letra é substituída pela seguinte no alfabeto.
- Hash: Resultado único e de tamanho fixo (ex: MD5, SHA-256).
- Hoax: Boatos ou mensagens alarmistas falsas espalhadas na rede.
- Scan: Processo de varredura em busca de vulnerabilidades em uma rede.
- Cookie: Pequeno arquivo de texto que armazena preferências de navegação do usuário.
- Log: Registro cronológico de eventos ou passos realizados em um sistema.

## 5. Pontos-Chave para Concursos
- Simétrica = 1 chave (mais rápida, foco em sigilo).
- Assimétrica = 2 chaves (mais segura para transações, foco em identidade e assinatura).
- Integridade = Garantida pelo Hash.
- Não Repúdio = Garantido pela Assinatura Digital (uso da chave privada do autor).