# FERSAN INVEST – Simulador de Fundos Imobiliários (EXCEO)

Planilha em Excel que simula investimentos em FIIs: do aporte mensal ao patrimônio acumulado e aos dividendos. Texto azul = editável; fundo cinza = calculado. Valores do arquivo são de exemplo.

**Arquivo:** `simulador_fii.xlsx` (abas **Simulador** e **Apoio**)

## O que a ferramenta responde

| Pergunta | Célula |
|---|---|
| Quanto investir por mês? | `C12` |
| Por quantos anos? | `C13` |
| Qual a taxa de rendimento mensal? | `C14` |
| Quanto de patrimônio vai acumular? | `C15` |
| Quanto vai receber de dividendos por mês? | `C16` |

Também mostra cenários de 2 a 30 anos (`B19:D23`) e a divisão do aporte entre seis tipos de FII conforme o perfil escolhido em `C25`, com gráfico de pizza.

## Fórmulas

- **VF:** `=VF(taxa_mensal; anos*12; -aporte)` calcula o patrimônio. Os dividendos são `patrimonio * rendimento_carteira`. Nos cenários, só muda o prazo (`$B19*12`).
- **PROCV com chave composta:** na aba Apoio a chave é `Perfil|Tipo`; no Simulador, `=PROCV(perfil&"|"&$B29; tab_perfil; 2; FALSO)` traz o percentual de cada tipo.

## Intervalos nomeados

`salario`, `rendimento_carteira`, `perc_sugestao`, `sugestao_aporte`, `aporte`, `anos`, `taxa_mensal`, `patrimonio`, `dividendos`, `perfil`, `tab_perfil`, `lista_perfis`.

## Percentuais por perfil

| Tipo | Conservador | Moderado | Arrojado |
|---|---|---|---|
| PAPEL | 40% | 32% | 20% |
| TIJOLO | 35% | 35% | 25% |
| HÍBRIDOS | 10% | 8% | 5% |
| FOFs | 10% | 5% | 5% |
| DESENVOLVIMENTO | 5% | 10% | 25% |
| HOTELARIAS | 0% | 10% | 20% |

Moderado vem do exemplo do Expert; Conservador e Arrojado são exemplos meus. **Não são recomendação de investimento.**

## Mudanças em relação ao Expert

Banner FERSAN INVEST, valores de exemplo próprios, dois perfis novos, conferência automática de 100% por perfil e validação de dados na lista de perfis.

## Prints

Mesma simulação em dois perfis: `prints/perfil_conservador.png` e `prints/perfil_arrojado.png`.
