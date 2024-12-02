---
title: "NSX - FAQ"
excerpt: "Retrouvez une foire aux questions des scénarios les plus fréquents concernant l'utilisation de NSX au sein de l'écosystème Hosted Private Cloud"
updated: 2024-12-02
---

## Objectif

**Retrouvez ci-dessous une foire aux questions pour répondre aux utilisations de NSX**.

## Foire aux questions - FAQ

> [!faq] 
> Quels sont les différences entre les packs d’assistance <a name="diffencepack"></a>
> > Tous les packs sont basés sur un décompte jours/heures, par exemple : 1 jour = 8 heures, 2 jours = 16 heures (parfois plus).
> > La première approche est la même pour tous les packs avec une phase de découverte, mais la durée du pack dépendra de la complexité de l'environnement et de la maturité de votre offre managée actuelle.
> > Cette question sera étudiée avec les équipes [Professional Services](/links/professional-services) lors d'un premier appel d'évaluation.
> >
> Comment puis-je protéger mes machines virtuelles directement exposées sur Internet avec une IP Publique ? <a name="public ip"></a>
> > Vous sécurisez vos flux avec le Distributed Firewall (sécurisation Nord/Sud ou Est/Ouest) de NSX ou utilisez l'un des Gateway Firewalls (sécurisation Nord/Sud).
> >
> Quelle est la date de fin de vie de NSX-v ? <a name="eofnsxv"></a>
> > VMware a décidé d'initier la fin de vie (EOL) de NSX-v depuis janvier 2022. OVHcloud a obtenu une extension de support jusqu'au 15 janvier 2025.
> >
> Est-il possible de faire du Border Gateway Protocol (BGP) ? <a name="bgp"></a>
> > Il est impossible de faire du BGP public (peer avec les routeurs internet OVHcloud).
> > Il est toutefois possible de faire du BGP (privé) avec un vRack via une passerelle Tier-0 ou une passerelle VRF de niveau 0, ou dans un tunnel IPsec via une Tier-0 uniquement.
> > 
> Est-ce que NSX-T est compatible BGP à travers IPSEC ? <a name="bgpoveripsec"></a>
> > Oui, à travers une VRF.
> >
> Quel est le changement concernant le système autonome BGP (AS) ?
> > Il est possible de positionner des AS numbers privés différents selon les passerelles Tier-0 ou les passerelles VRF de niveau 0.
> >
> Peut-on mettre un pare-feu virtuel devant le Tier-0 dans le même vSphere managé ?
> > Vous pouvez tout à fait déconnecter les interfaces publiques de la T0 et interconnecter celles-ci via un réseau privé ou une appliance de sécurité exposée en direct sur internet. Notez qu'il existe dans la T0 un firewall intégré configurable via l'interface NSX, Gateway Firewall.
> >
> Quelle est la différence entre une passerelle Tier-0 et une Tier-1 ? <a name="t0vst1">
> > Dans la conception VMware, une Tier-1 est toujours attachée à une Tier-0.
> > Les flux passent par une Tier-0 pour aller au réseau externe.
> > Tous les éléments devant rester à l'intérieur (en local) de la plateforme Vsphere managée sont routés par la Tier-1.
> >
> Comment puis-je ajouter une autre Tier-0 Gateway ? <a name="addt0gw"></a>
> > Il est actuellement impossible d'ajouter une nouvelle Tier-0 Gateway.
> > Selon les besoins, il est possible de créer une instance virtuelle de Tier-0 appelée VRF. Cette VRF ne pourra pas être connectée sur internet.
> >
> Le bouton "Edit" dans NSX pour une Tier-0 est désactivé, comment puis-je configurer la Gateway publique ? <a name="publicgateway"></a>
> > C'est impossible par défaut. Les Tier-0 Gateways sont hébergées chacune sur un host différent, HA (High Availability) est activée et une IP virtuelle (VIP) est configuré entre les 2 EDGES afin de maintenir la continuité de service. La partie HA est déjà préconfigurée par OVHcloud.
> >
> Puis-je configurer une Tier-0 Gateway active-active afin d’avoir une double bande passante ("garantie" 10+10=20Gb/s et "théorique" 25+25=50Gb/s) ? 
> > Non, c'est impossible par défaut, la configuration est gérée par OVHcloud et se fait en mode actif/passif avec un VIP (10 Gbp/s de bande passante garantie).
> >
> Est-il possible de se connecter à la Edge en SSH pour effectuer un diagnostic ou de la capture de paquets ? <a name="t0gwdoublebw"></a>
> > Non, c'est impossible, que ce soit pour des informations sur Tier-0 ou Tier-1. Il existe dans NSX des outils de troubleshooting.
> >
> Quel est le nombre maximum d'interfaces (segments connectés) sur une Tier-1 Gateway ? <a name="t1interface capacity"></a>
> > Cette information dépend de la version de NSX en production sur l'infrastructure. Les valeurs maximales se trouvent sur le site Broadcaom dédié : <https://configmax.broadcom.com/home>.
> >
> Comment puis-je ajouter des IP publiques ? <a name="addpublicicip"></a>
> > L'ajout d'IP publiques supplémentaires peut se faire via le routage "next hop" en spécifiant comme ressource l'environnement VMware Hosted Private Cloud et en `next hop` l'IP virtuelle (VIP) publique de la Tier-0 (T0).
> >
> Est-ce que les blocs d’adresses IP peuvent être utilisés/distribués entre deux Datacenters VMware dans un même Hosted Private Cloud ? <a name="ipblockdistribution"></a>
> > Les blocs d'adresses IP sont dépendants de l'environnement VMware Hosted Private Cloud et non du Datacenter virtuel. Il est donc possible d'utiliser le même bloc d'adresses IP entre plusieurs datacentres virtuels (sans aucune modification).
> > Attention, si vous disposez de plusieurs Datacenters virtuels, un bloc d'IP publiques routé sur l'IP virtuelle (VIP) de votre Tier-0 (T0) ne pourra pas être utilisé dans un `VM Network` d'un autre Datacenter virtuel. Il est attaché à la VIP et non plus au `VM Network`.
> > 
> Comment sont gérées les IP lors de la migration ? <a name="managemigrationip"></a>
> > Vous trouverez, dans le [guide de migration](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/service-migration-vdc), comment déplacer votre IP existante depuis votre plateforme NSX-v et la router vers l'IP attachée à la partie Tier-0 (T0).
> > Lorsqu’un Datacenter Virtuel NSX-T est livré, nous déployons et configurons un nouveau bloc IP pour NSX Tier-0 (T0) que nous dédions à la VIP. C'est vers cette VIP que vous pourrez router le bloc IP. 
> >
> Pour la migration vDC, il faut passer le datastore en global. Un retour en arrière est-il possible sur cette configuration ? <a name="vdcmigration"></a>
> > Le datastore global est géré au niveau de l'espace client ou de l’API OVHcloud.
> > Cela vous permet de globaliser votre datastore qui sera visible depuis votre nouveau vDC. Il vous permet de faire un `Compute` vMotion et non un `Storage` vMotion des machines virtuelles.
> > Il n'est pas possible de le sortir de ce mode. Il vous faudra commander un nouveau datastore et y appliquer un vMotion pour le libérer globalement.
> >
> Allez-vous fournir des formations et de la documentation pour améliorer les compétences NSX-T ? <a name="docandtrainingnsxt"></a>
> >
> > - [Premiers pas avec NSX](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/nsx-01-first-steps)
> > - [VMware on OVHcloud](/products/hosted-private-cloud-hosted-private-cloud-powered-by-vmware)
> >
> Si une migration NSX-v a été planifiée vers une solution tierce pfSense, doit-on repartir sur une demande de création d'un nouveau Datacenter virtuel sans NSX-v ? Peut-on le faire sur le Datacenter virtuel existant ? <a name="nsxtmigrationpfsense"></a>
> > Dans ce cas, vous n'avez pas besoin de commander un nouveau vDC, mais assurez-vous de désactiver toutes vos fonctionnalités NSX-v afin que OVHcloud puisse désactiver le composant.
> >
> 
> La migration des IP peut-elle se faire IP par IP ou par bloc IP ? <a name="ipmigrationperblock"></a> 
> > La migration d'IP est effectuée par bloc, vous changez le *next stop* du bloc IP, le bloc global est transitionné vers la partie NSX.
> >
> Cette migration interrompt-elle les services portés par NSX ? Si oui, combien de temps ? <a name="ipmigrationinterruption"></a>
> > Cela dépendra des services utilisés. Par exemple, si vous utilisez des tunnels IPSEC et des IP publiques, vous devrez déplacer vos workloads et reconfigurer le bloc IP que vous aviez sur votre infrastructure NSX-v vers votre infrastructure NSX-T. 
> > Si vous utilisez NSX-v pour du firewalling, vous pouvez avoir la configuration sur les 2 environnements.
> > Le temps d'arrêt dépend donc de la complexité de votre environnement.
> >
> Quel sera le débit des cartes des edge-nodes, sachant que le Tier-0 (T0) sera mutualisé ? <a name="bandwidthedgenode"></a>
> > Cela dépendra des services activés (LoadBalancer/NAT/Firewall, etc.). Les débits et maximums sont dépendants de la version de NSX et disponibles sur le site de Broadcom.
> >
> Est-ce que le vRack fonctionne avec les NSX-T ?  <a name="vrackwithnsxt"></a>
> > Oui, le vRack fonctionne avec NSX-T.
> > Vous avez la possibilité d'y accéder de la même manière à partir de portgroups vlan dans vSphere ou à partir de segments VLAN dans NSX-T.
> >
> Le cluster de NSX Edges aura-t-il accès au vRack OVHcloud ? <a name="vrackaccess"></a>
> > Le cluster de NSX Edges est bien compatible avec un vRack OVHcloud. Vous pouvez ajouter votre Datacenter virtuel qui porte NSX-T dans le vRack de votre choix. Retrouvez plus d'informations sur [cette page](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vrack_and_hosted_private_cloud).
> >
> Puis-je configurer la haute disponibilité sur les NSX Edges ? <a name="ha"></a> 
> > Non, la gestion des NSX Edges est effectuée par OVHcloud en mode Actif Passif.
> >
> Est-il possible d'avoir plusieurs edge clusters ? <a name="multipleedgeclusters"></a>  
> > Aujourd'hui, 1 seul cluster NSX-T Edge est déployé.
> >
> Actuellement, nous avons 300 edges et environ 5000 RDP simultanés. La configuration moyenne "4 vcpu / 8 Go RAM / 200 Go" va-t-elle tenir pour les flux ? <a name="averageconfiguration"></a>
> > Le dimensionnement dépendra des services que vous activerez ou consommerez sur vos edges (firewall ou load balancing...).
> > Aujourd'hui, les Edge sont de taille Medium. Les maximums et dimensionnements sont disponibles sur le site de Broadcom.
> >
> Je viens de créer un cluster et je voudrais le configurer pour NSX en API. Comment faire ?
> > Il faut utiliser cette route, après avoir récupéré le cluster ID que vous venez de créer.
> >
> > > [!api]
> > >
> > > @api {v1} /dedicatedCloud POST /dedicatedCloud/{serviceName}/datacenter/{datacenterId}/cluster/{clusterId}/nsxt 
> > 
> > 
> > 
> Puis-je utiliser l’API OVHcloud pour configurer et utiliser mes NSX Edges en API ? <a name="api"></a>
> > Oui, il est possible de le faire, voici un exemple des appels API que vous pouvez utiliser au sein de l'univers **/dedicatedcloud** :
> > Récupérer le Edge ID :
> > > [!api]
> > >
> > > @api {v1} /dedicatedCloud GET /dedicatedCloud/{serviceName}/datacenter/{datacenterId}/nsxtEdge/{nsxtEdgeId}
> > >
> > Vous pouvez par exemple tester la résilience en simulant la panne d'un des nodes Edge du cluster :
> > > [!api]
> > >
> > > @api {v1} /dedicatedCloud POST /dedicatedCloud/{serviceName}/datacenter/{datacenterId}/nsxtEdge/{nsxtEdgeId}/resilience/enable 
> > >  
> > 
> Que faire de mes options de sauvegarde Veeam et de replication Zerto ? Sont-elles toujours compatibles avec NSX ? <a name="veeamzerto"></a>
> > Oui, mais il faudra les reconfigurer après la migration de votre Datacenter virtuel.
> >
> Est-il possible de faire cohabiter NSX-v et NSX-T durant la phase de transition ? <a name="nsxtwithnsxv"></a>
> > Il est possible d'obtenir NSX-T si vous commandez un nouveau Datacenter virtuel dans votre Hosted Private Cloud. Vous aurez donc au sein de la même infrastructure 2 Datacenters virtuels, l'un avec NSX-v et l'autre avec NSX-T.
> > Veuillez noter que la commande du nouveau vDC déclenchera automatiquement le mécanisme de remboursement pour le mois à venir.
> >
> Pouvons-nous utiliser "migration coordinator" pour la migration entre NSX-v et NSX-T ? <a name="nsxmigrationcoordinator"></a>
> > Cet outil nécessite des droits d'administration très forts sur l'environnement, l'équipe Professional Services peut valider l'exécution et la duplication. Dans cet outil, il est important de noter que de nombreux éléments ne sont pas pris en charge (options, règles existantes dans NSX-v).
> > La phase de reproduction nécessiterait beaucoup d'adaptations de votre part, ce n'est donc pas un outil recommandé dans la migration chez OVHcloud.
> >
> Pourquoi l'interface de gestion de NSX est-elle réalisée via un endpoint `https://nsxt.pcc-xxx-xxx-xxx-xxx.ovh.com` distinct ? <a name="nsxterraform"></a>
> > L'interface NSX est indépendante et non liée à l'interface de vSphere. C'est pourquoi nous avons créé un endpoint dédié pour l'atteindre.
> >
> Est-il possible de faire communiquer un routeur NSX Edge entre 2 environnements Hosted Private Cloud ? <a name="nsxedge"></a>
> > Oui, c'est possible, via le vRack par exemple, ou via le réseau public et les VIP des Edges Cluster.
> >
> Réalisez-vous des backups des configs NSX-T, y compris le paramétrage manuel du client ? <a name="nsxbackupmanualconfiguration"></a>
> > Oui, OVHcloud réalise des sauvegardes.
> > Cette sauvegarde n'est pas destinée à la restauration lors d'une mauvaise manipulation, mais de support en cas d'incident des différents contrôleurs NSX-T.
> > 
> Est-il possible d'avoir la livraison d'un vDC NSX-T dans un VMware vSphere managé d'année 2016, existera-t-il des problèmes lors de la livraison ? <a name="nsxtinto2016pcc"></a>
> > Oui, c'est possible, il n'y a pas de contraintes actuellement.
> >
> Des limitations supplémentaires sont-elles présentes dans un contexte SecNumCloud ? <a name="snclimitations"></a>
> > Il n’y a pas de limitations supplémentaires par rapport à un environnement non qualifié SecNumCloud.
> >
> La gestion des sauvegardes est-elle différente sur l'offre qualifiée SecNumCloud ? <a name="semnumcloudbackupoutside"></a>
> > Il n'existe pas de différence entre les sauvegardes dans les environnements qualifiés SecNumCloud et non SecNumCloud.
> >
> Pendant la phase de migration, devra-t-on payer en double notre plateforme durant un mois ? <a name="priceduringmigration"></a>
> > OVHcloud vous remboursera 1 mois pour le datacenter virtuel ajouté sur votre prochaine facture après la commande (1 mois = 30 jours).
> >
> Pouvons nous utiliser le Load Balancer Advanced (AVI) ou le Gateway IDS/IPS ? <a name="pricealbandipsids"></a>
> > Non, ces fonctionnalités ne sont pas incluses.
> > 
> Pouvons nous utiliser l'IDS/IPS distribué ? <a name="pricealbandipsids"></a>
> > oui.

## Aller plus loin

[Premiers pas avec NSX](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/nsx-01-first-steps).

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en oeuvre de nos solutions, contactez votre commercial ou cliquez sur [ce lien](/links/professional-services) pour obtenir un devis et demander une analyse personnalisée de votre projet à nos experts de l’équipe Professional Services.

Échangez avec notre [communauté d'utilisateurs](/links/community).