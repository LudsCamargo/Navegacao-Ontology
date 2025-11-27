# Navegacao-Ontology

Overview

A Nautical Ontology é uma representação semântica dos conceitos centrais em Estudos Náuticos e Navegação à Vela.
Esta ontologia modela embarcações, seus componentes, tipos de vela, manobras, condições ambientais, tripulação e eventos náuticos.

Foi projetada para:

apoiar pesquisas acadêmicas na área náutica;

servir como base para pequenas empresas, como escolas de vela e clubes;

permitir raciocínio automatizado, consultas SPARQL e interoperabilidade com dados externos (DBpedia/Wikidata).

______________________________________________________________________________________________________________
 Features

Estrutura Hierárquica Completa
Organiza embarcações, velas, componentes e papéis da tripulação em classes e subclasses.

Modelagem de Navegação
Inclui manobras (tack, jibe, orçar, arribar) e condições ambientais (vento, maré, estado do mar).

Ligações a Fontes Externas
Inclui rdfs:seeAlso para DBpedia/Wikidata para classes como Veleiro, Vela, Mastro, Spinnaker, Regata etc.

Axiomas Lógicos OWL
Permite inferências como:

Regata usa embarcação do tipo Veleiro.

Toda Embarcação tem pelo menos um ComponenteEmbarcacao.

______________________________________________________________________________________________________________
 Classes e Subclasses
Embarcação

Embarcacao (classe raiz)

Veleiro

Monocasco

Multicasco

Catamara

Trimaran

BarcoDeApoio

BoteInflavel

Componentes da Embarcação

ComponenteEmbarcacao (raiz)

Vela

GrandeVela

Genoa

Spinnaker

Mastro

Quilha

Leme

Casco

Cabine

Tripulação

Tripulacao (raiz)

Comandante

Timoneiro

Proeiro

Tripulante

Manobras Náuticas

Manobra (raiz)

ViradaDeBorda (tack)

Jibe (gybe)

IcarVela

RecolherVela

Condições Ambientais

CondicaoAmbiental (raiz)

Vento

Correnteza

Mare

EstadoDoMar

Visibilidade

Equipamentos de Segurança

EquipamentoDeSeguranca (raiz)

ColeteSalvaVidas

RadioVHF

Sinalizador

Eventos Náuticos

EventoNautico (raiz)

Regata

AulaDeVela

Treinamento

Passeio

Localização Marítima

LocalizacaoMaritima (raiz)

Baia

Canal

MarAberto

PortoMarina

______________________________________________________________________________________________________________
Propriedades (Object Properties)

possuiComponente
Embarcacao → ComponenteEmbarcacao

eTripuladaPor
Embarcacao → Tripulacao

executaManobra
Tripulacao → Manobra

ocorreEm
EventoNautico → LocalizacaoMaritima

usaEmbarcacao
EventoNautico → Embarcacao

temCondicaoAmbiental
LocalizacaoMaritima → CondicaoAmbiental

temEquipamentoDeSeguranca
Embarcacao → EquipamentoDeSeguranca


______________________________________________________________________________________________________________
Propriedades de Dados (Data Properties)

temComprimento (float)

temLargura (float)

anoConstrucao (gYear)

nomeEmbarcacao (string)

velocidadeDoVento (float)

direcaoDoVento (string)

alturaOndas (float)

horarioEvento (dateTime)

______________________________________________________________________________________________________________
 Axiomas Lógicos (OWL)
Definição de Embarcação
Embarcacao ⊑ ∃possuiComponente.ComponenteEmbarcacao


Toda embarcação possui ao menos um componente.

Regata
Regata ⊑ EventoNautico ⊓ ∃usaEmbarcacao.Veleiro


Uma regata envolve pelo menos um veleiro.

Manobras feitas pela tripulação
Tripulacao ⊑ ∀executaManobra.Manobra

Veleiro como embarcação à vela
Veleiro ⊑ Embarcacao

______________________________________________________________________________________________________________
 Links Externos (DBpedia / Wikidata)

Algumas classes incluem:

rdfs:seeAlso apontando para referências confiáveis.
Exemplos:

Veleiro → DBpedia: Sailing

Vela → DBpedia: Sail

Spinnaker → DBpedia: Spinnaker

Mastro → DBpedia: Mast

Keel → Wikipedia

Rudder → DBpedia

Regata → DBpedia: Regatta

🧪 Exemplo de Query SPARQL

Obter todos os componentes utilizados por embarcações:

SELECT ?emb ?comp
WHERE {
  ?emb rdf:type ex:Embarcacao .
  ?emb ex:possuiComponente ?comp .
}

______________________________________________________________________________________________________________
  Uso

Use um reasoner (HermiT recomendado) para inferências.

Utilize SPARQL para consultas semânticas:

"Quais são as manobras ensinadas em aulas de vela?"

"Quais embarcações aparecem em regatas?"

"Que componentes estruturais existem em veleiros?"

 ______________________________________________________________________________________________________________
 Contribuição

Contribuições são bem-vindas!

Faça um fork.

Crie uma branch.

Envie um pull request com a descrição das mudanças.

______________________________________________________________________________________________________________

 Agradecimentos

Desenvolvido com Protégé e OWL 2.

Inspirado pela tradição náutica, literatura marinheira e bases DBpedia/Wikidata.

Baseado no modelo de documentação do projeto Pizza Ontology.
