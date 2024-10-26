# JAS-Haunted-Castle-PvP

Add or merge the contents into the respective files...

  1) To spawn the castle add "Haunted_JAS.json" to your custom folder and add "custom/Haunted_JAS.json" to the static object spawner array in cfggameplay.json
      -I adjusted the heights of the buildings and got rid of the front gate... so nobody gets out.

          "objectSpawnersArr": ["custom/haunted_JAS.json"],
     
  2) To have the new buildings spawn loot:
     -Merge the contents of the mapgrouppos.xml here with the server's. (lets the game know these are loot spots)
     -Merge the contents of the mapgroupproto.xml here with the server's (lets the game know the loot spawn points within the buildings)

  3) Add the Slasher Character gear preset files to cfggameplay.json
      -Female characters spawn as the Scream Queen, and male characters spawn 50/50 as either Freddy or Jason. Knives for everyone

          "spawnGearPresetFiles": ["custom/Jason.json", "custom/Freddy.json", "custom/Scream_Queen.json"],

  4) Load/merge the remaining zombie files from Bhaalshad's
      -Modify "ZmbM_SkaterYoung_Blue" in cfgspawnabletypes.xml

          <type name="ZmbM_SkaterYoung_Blue">
          		<attachments preset="ZombieWitchHats" />
          		<attachments><item name="CrookedNose" /></attachments>
          		<attachments><item name="HighCapacityVest_Black" /></attachments>
          		<attachments><item name="BomberJacket_Black" /></attachments>
          		<attachments><item name="CargoPants_Black" /></attachments>
          		<cargo chance="0.25"><item name="TetracyclineAntibiotics" /></cargo>
          		<cargo chance="0.25"><item name="EasterEgg" /></cargo>		
          		<cargo preset="foodArmy" />
          </type>

      -Modify "zombie_territories.xml" in the "env" folder to have the five spawn locations

          <zone name="InfectedWitch" smin="4" smax="8" dmin="4" dmax="10" x="12111.0" z="12694.0" r="140"/>
          <zone name="InfectedWitch" smin="4" smax="8" dmin="4" dmax="10" x="12240.0" z="12638.0" r="140"/>
          <zone name="InfectedWitch" smin="4" smax="8" dmin="4" dmax="10" x="12228.0" z="12550.0" r="140"/>
          <zone name="InfectedWitch" smin="4" smax="8" dmin="4" dmax="10" x="12088.0" z="12603.0" r="140"/>	
          <zone name="InfectedWitch" smin="4" smax="8" dmin="4" dmax="10" x="12207.0" z="12749.0" r="140"/>

      -Add "InfectedWitch" to the events.xml

           <event name="InfectedWitch">
                <nominal>150</nominal>
                <min>25</min>
                <max>250</max>
                <lifetime>3</lifetime>
                <restock>0</restock>
                <saferadius>100</saferadius>
                <distanceradius>50</distanceradius>
                <cleanupradius>100</cleanupradius>
                <flags deletable="0" init_random="0" remove_damaged="1"/>
                <position>player</position>
                <limit>custom</limit>
                <active>1</active>
                <children>
                    <child lootmax="5" lootmin="0" max="0" min="100" type="ZmbM_SkaterYoung_Blue"/>
                </children>
           </event>

      -Randomize the zombie headgear by adding the lines below to cfgrandompresets.xml

            <attachments chance="1.00" name="ZombieWitchHats"> 
                <item name="WitchHat" chance="0.33" />
                <item name="GreatHelm" chance="0.33" />
                <item name="PumpkinHelmet" chance="0.33" />
            </attachments>

     -Fog effect, add the following in cfgEffectArea.json

            {   "AreaName": "Haunted-Area-1", 
                "Type": "SpookyArea", 
                "TriggerType": "EffectTrigger",
                "Data": { 
                    "Pos": [ 12167, 0, 12634 ],
                    "Radius": 100,
                    "PosHeight":50,
                    "NegHeight": 20,
                    "InnerRingCount": 1,
                    "InnerPartDist": 25,
                    "OuterRingToggle": 1, 
                    "OuterPartDist": 40,
                    "OuterOffset": -80, 
                    "VerticalLayers": 0,
                    "VerticalOffset": 0,
                    "ParticleName": "graphics/particles/spooky_mist"
                    },
                "PlayerData": {
                    "AroundPartName": "graphics/particles/smoke_bonfire",
                    "TinyPartName": "graphics/particles/contaminated_area_gas_around_tiny",
                    "PPERequesterType": "PPERequester_GlassesSportBlack"
                }
            },
            {   "AreaName": "Haunted-Area-2", 
                "Type": "SpookyArea", 
                "TriggerType": "EffectTrigger",
                "Data": { 
                    "Pos": [ 12167, 0, 12634 ],
                    "Radius": 100,
                    "PosHeight":50,
                    "NegHeight": 20,
                    "InnerRingCount": 1,
                    "InnerPartDist": 25,
                    "OuterRingToggle": 1, 
                    "OuterPartDist": 60,
                    "OuterOffset": -120, 
                    "VerticalLayers": 1,
                    "VerticalOffset": 25,
                    "ParticleName": "graphics/particles/spooky_mist"
                    },
                "PlayerData": {
                    "AroundPartName": "graphics/particles/smoke_bonfire",
                    "TinyPartName": "graphics/particles/contaminated_area_gas_around_tiny",
                    "PPERequesterType": "PPERequester_GlassesSportBlack"
                }
            }
