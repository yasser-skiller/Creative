<template>
 <div>
   <AppNav/>
   <Header/>
   <Cources/>
   <Why/>
   <Ordny/>
   <Channel/>
    <Contact/>
   <Info/>
   <Team/>
   <InfoSce/>
   <LastNews/>
   <AppFooter/>
 </div>
</template>

<script>
import AppNav from '@/components/AppNav';
import Header from '@/components/Header';
import Cources from '@/components/Cources';
import Why from '@/components/Why';
import Ordny from '@/components/Ordny';
import Channel from '@/components/Channel';
import Contact from '@/components/Contact';
import Info from '@/components/Info';
import Team from '@/components/Team';
import InfoSce from '@/components/InfoSce';
import LastNews from '@/components/LastNews';
import AppFooter from '@/components/AppFooter';

export default {
  components:{
    AppNav,
    Header,
    Cources,
    Why,
    Ordny,
    Channel,
    Contact,
    Info,
    Team,
    InfoSce,
    LastNews,
    AppFooter,
  },
}
</script>
