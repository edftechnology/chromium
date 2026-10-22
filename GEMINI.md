# Diretrizes do projeto Thesis

- Ao concluir cada solicitação de trabalho, emita um beep no terminal (por exemplo, `printf '\\a'`) após terminar as verificações e operações solicitadas.
- Sempre que alterar uma GUI, reinicie o serviço que a disponibiliza ou a execução da própria GUI, conforme aplicável, e valide que a versão atualizada está respondendo antes de concluir. O usuário não deve continuar usando uma execução antiga da interface.
- Se houver um fluxograma Dia associado ao código ou processo documentado, atualize-o junto com as alterações no código para mantê-lo sincronizado com o comportamento implementado.

## Segurança e auditoria de código

### Diretrizes gerais

- Priorizar a segurança, a integridade e a confidencialidade do código-fonte.
- Verificar possíveis vulnerabilidades antes de concluir alterações relevantes.
- Utilizar o plugin `codex-security` quando disponível e apropriado.
- Nunca expor senhas, tokens, chaves de API ou outras credenciais.
- Não executar comandos destrutivos sem autorização explícita.
- Não modificar arquivos durante auditorias solicitadas como somente leitura.

### Auditoria de segurança

Quando o usuário solicitar uma auditoria de segurança, verificar:

1. Vulnerabilidades no código Python e Shell Script.
2. Exposição de senhas, tokens e chaves de API.
3. Dependências com vulnerabilidades conhecidas.
4. Comandos perigosos ou destrutivos.
5. Riscos de injeção de comandos e execução arbitrária.
6. Configurações inseguras e permissões excessivas.
7. Possíveis problemas de segurança nos submódulos Git.

### Relatório de segurança

Apresentar os resultados contendo:

- Severidade: crítica, alta, média, baixa ou informativa.
- Arquivo e linha afetados.
- Descrição da vulnerabilidade e evidências.
- Impacto potencial.
- Recomendação de correção.
- Ferramentas efetivamente utilizadas.
- Limitações da auditoria e verificações não realizadas.

Não afirmar que o projeto está completamente seguro apenas porque nenhuma vulnerabilidade foi identificada.

### Eficiência de tokens e contexto

- Evitar auditorias completas quando a alteração for pequena e localizada.
- Priorizar a análise dos arquivos modificados.
- Reutilizar resultados válidos de verificações anteriores quando apropriado.
- Evitar leituras repetidas e desnecessárias.
- Executar auditorias completas quando explicitamente solicitado ou quando houver mudanças relevantes para a segurança.

## Gestão de risco de modelos (MRM)

Aplique estas orientações quando o sistema usar métodos quantitativos, estatísticos, de aprendizado de máquina ou abordagens semelhantes para produzir estimativas, classificações, recomendações ou decisões. Ajuste o rigor à finalidade, materialidade, exposição, complexidade e contexto de uso; não imponha controles desnecessários a ferramentas sem risco de modelo relevante.

- Registre, conforme o risco, finalidade e uso previsto, responsável, versão, dados e linhagem, premissas, limites de uso, limitações conhecidas, dependências, critérios de desempenho, revisões e aprovações.
- Antes de uso material, avalie a adequação conceitual, os dados, a implementação e os resultados. Use testes reproduzíveis, comparações ou referências independentes quando apropriado; busque crítica objetiva por pessoa qualificada que não seja a única autora ou responsável pelo modelo.
- Monitore desempenho, qualidade e mudanças nos dados e no contexto. Defina sinais de alerta, resposta a desvios, revisão de mudanças e critérios para limitar, recalibrar, revalidar, suspender ou retirar o modelo.
- Comunique incerteza, premissas, limitações e restrições de uso. Não prometa precisão, imparcialidade, validação ou conformidade sem evidência; mantenha supervisão humana adequada ao impacto da decisão.
- Preserve documentação e evidências suficientes para reproduzir e auditar decisões, testes e mudanças. Proteja dados pessoais, confidenciais e credenciais; não os inclua em logs, prompts, commits ou artefatos sem autorização e necessidade.
- Considere interdependências, modelos de terceiros e métodos determinísticos de impacto material. Aplique controles equivalentes quando o risco justificar, mesmo que a ferramenta não seja formalmente classificada como modelo.
- Consulte `docs/references/README.md` quando disponível, confirme a edição e a jurisdição aplicáveis e trate os materiais como orientação contextual, não como obrigação legal universal. A orientação interagências dos EUA de 2026 não abrange modelos generativos/agênticos; avalie controles adequados ao contexto. Verifique também datas de vigência antes de afirmar aplicabilidade.
