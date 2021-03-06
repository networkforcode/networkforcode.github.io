---
layout: post 
title: "Network Automation - Topologia Campus Fabric"
date:   2020-03-30
---

<p class="intro"><span class="dropcap">B</span>uenas NetCode. Neste artigo vamos falar sobre um modelo de design que está em alta nas novas topologias de enterprise network. Fique à vontade para entrar em contato comigo pelo Linkedin, estamos todos aqui para aprendermos juntos.</p>

<p>Vamos lá, esse conceito nada mais é que você centralizar sua topologia em apenas uma única gerência, essa gerência leva em consideração o uso do DNA CENTER (tratando-se de Cisco), o que roda por trás do DNA é o Apic. O uso dessa ferramenta de SDN é fazer com que, você só faz o uso do acesso manual a cada appliance quando ocorre uma falha muito crítica na qual o software não consegue resolver. O DNA faz o uso de sua gerência via interface web.</p>

<p>Quando falamos de campus fabric, estamos falando de duas camadas, underlay e overlay. Quando dividimos a infraestrutura em duas camadas, em underlay não é necessário alocar hardware robusto para se conectar com alguma cloud provider.</p>

<p>Vale ressaltar que não é apenas wi-fi que irá fazer com que você se conecte com ambientes externos. Como estamos falando de enterprise, devemos focar em conceitos apenas de on-premises neste momento.</p>

<img src="{{ '/assets/img/artigo02/img01.jpg' | prepend: site.baseurl }}" alt=""> 

<p>Overlay – Seria a base onde é alocado uma parte relacionada à control-plane, ou seja, tudo que for baseado em software ficaria alocado nesta camada. Vale ressaltar que os componentes do fabric estariam alocados no overlay, já os componentes do edge (SD-ACCESS) estariam alocados no underlay. Componentes do fabric estaria no data center e os componentes do edge devices ficariam em uma infraestrutura próxima (local) aos usuários.</p>

#### Underlay

<p>Seria os componentes físicos necessários que sua infraestrutura tem que ter, as caixas que se alocam nesta camada não tem muita inteligência, as features mais robustas serão arrancadas desses appliances pelo fato de que esses devices irão fornecer apenas conectividade para poder integrar com sua camada superior.</p>

### Componentes do Campus Fabric

<img src="{{ '/assets/img/artigo02/img02.jpg' | prepend: site.baseurl }}" alt=""> 

#### Identify services
<p>Seria a validação do acesso que você irá policiar o device para ter acesso à rede, seria o ISE.</p>

#### NDP
<p>Seria uma ferramenta de monitoramento da rede, não só monitora os incidentes mas também faz um cross-checking, recolhe as informações e passa a resposta do por que aquele incidente ocorreu, ou seja, ele tem uma visão de monitoramento da rede como um fim a fim.</p>

#### Fabric Border Nodes
<p>Seriam os devices que estão conectados com a WAN, ou seja, links externos layer 3.</p>

#### Fabric Edge Nodes
<p>Seriam appliances que estariam gerenciando a camada de acesso, ou seja, seriam devices com gerências SD-ACCESS.</p>

#### Control-Plane Nodes
<p>É o cara que vai estar conectado com a gerência do DNA, e ele irá enviar a execução de alguma alteração de configuração para seus Border Nodes e Edge Nodes. Ou seja, toda essa parte de software será executada pelo control plane.</p>

<p>Para você mudar o custo de OSPF para ter outro dimensionamento na sua rede, ou até mesmo alterar a politica de QoS sem precisar acessar device por device, você iria atribuir o uso do design Fabric Capacity Planning que seria exatamente estes conceitos que estamos descrevendo.</p>

<p>Dica: Os componentes que que rodam em overlay, não necessariamente precisam ser equipamentos físicos, quando a empresa tem um budget a mais, a solução mais apropriada é comprar um servidor UCS da Cisco e virtualizar esses serviços.</p>

<p>E aí, o que achou deste conceito de design voltado para enterprise usando ferramentas de SDN?</p>

