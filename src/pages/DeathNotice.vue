<template>
  <q-page padding class="flex flex-center">
    <div class="row q-col-gutter-md">
      <div class="col-12 col-md-6">
        <q-card style="min-width: 500px;">
          <q-card-section>
            <q-list>
              <q-item-section>
                <div class="text-h6 text-center q-pb-md">偏好设置</div>
              </q-item-section>
            </q-list>
          </q-card-section>
        </q-card>
      </div>
      <div class="col-12 col-md-6">
        <q-card style="min-width: 500px;">

        </q-card>
      </div>
    </div>
  </q-page>
</template>

<script>
import html2canvas from "html2canvas";
export default {
  name: "DeathNotice",
  data () {
    return {
      weapons: [
        'ak47',
        'ammobox',
        'ammobox_threepack',
        'armor',
        'armor_helmet',
        'assaultsuit',
        'aug',
        'awp',
        'axe',
        'bayonet',
        'bizon',
        'breachcharge',
        'breachcharge_projectile',
        'bumpmine',
        'c4',
        'controldrone',
        'cz75a',
        'deagle',
        'decoy',
        'defuser',
        'diversion',
        'dronegun',
        'elite',
        'famas',
        'firebomb',
        'fists',
        'fiveseven',
        'flashbang',
        'flashbang_assist',
        'frag_grenade',
        'g3sg1',
        'galilar',
        'glock',
        'grenadepack',
        'grenadepack2',
        'hammer',
        'healthshot',
        'heavy_armor',
        'hegrenade',
        'helmet',
        'hkp2000',
        'incgrenade',
        'inferno',
        'kevlar',
        'knife',
        'knife_bowie',
        'knife_butterfly',
        'knife_canis',
        'knife_cord',
        'knife_css',
        'knife_falchion',
        'knife_flip',
        'knife_gut',
        'knife_gypsy_jackknife',
        'knife_karambit',
        'knife_m9_bayonet',
        'knife_push',
        'knife_skeleton',
        'knife_stiletto',
        'knife_survival_bowie',
        'knife_t',
        'knife_tactical',
        'knife_ursus',
        'knife_widowmaker',
        'knifegg',
        'm4a1',
        'm4a1_silencer',
        'm4a1_silencer_off',
        'm249',
        'mac10',
        'mag7',
        'molotov',
        'mp5sd',
        'mp7',
        'mp9',
        'negev',
        'nova',
        'p90',
        'p250',
        'p2000',
        'planted_c4_survival',
        'prop_exploding_barrel',
        'radarjammer',
        'revolver',
        'sawedoff',
        'scar20',
        'sg556',
        'shield',
        'smokegrenade',
        'snowball',
        'spanner',
        'ssg08',
        'stomp_damage',
        'tablet',
        'tagrenade',
        'taser',
        'tec9',
        'ump45',
        'usp_silencer',
        'usp_silencer_off',
        'xm1014',
        'zone_repulsor'
      ],
      prefixIcons: [
        'revenge',
        'domination',
        'blindkill'
      ],
      suffixIcons: [
        'noscope',
        'jumpkill',
        'throughsmoke',
        'penetrate',
        'headshot',
        'suicide',
        'kill360'
      ],
      dNotices: [
        {
          attacker: 'Attacker',
          attackerCamp: 'T',
          victim: 'Victim',
          victimCamp: 'CT',
          weapon: 'ak47',
          prefixIcon: ['blindkill'],
          suffixIcon: ['headshot'],
          redBorder: false,
          hide: false
        },
        {
          attacker: '中文字体样式.gg',
          attackerCamp: 'CT',
          victim: 'Purp1e',
          victimCamp: 'T',
          weapon: 'awp',
          prefixIcon: ['revenge', 'blindkill'],
          suffixIcon: [],
          redBorder: true,
          hide: false
        }
      ],
      generating: false,
      w: 1920,
      h: 1080,
      hidpi: 2,
      prefix: '击杀-',
      current: 0,
      fold: false
    }
  },
};
</script>

<style scoped></style>
