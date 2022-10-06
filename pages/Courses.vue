<template>
  <div>
    <AppNav/>
    <CoursesPage/>
    <AppFooter/>
  </div>
</template>

<script>
import AppNav from '@/components/AppNav';
import CoursesPage from '@/components/CoursesPage';
import AppFooter from '@/components/AppFooter';


export default {
 components:{
  AppNav,
  CoursesPage,
  AppFooter
 },
}
</script>
