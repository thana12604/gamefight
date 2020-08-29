<template>
<div>
    <img :src="Logo" width="800" height="280" class="img-fluid mx-auto">
    <br />
    <br />
    <br />
    <button v-on:click="randomHero" class="btn btn-secondary">Start</button><p></p>
    <button v-on:click="attack" class="btn btn-danger mb-4">Attack</button>
    <button v-on:click="special" class="btn btn-warning mb-4">SpecialAttack</button>
    <button class="btn btn-info mb-4" @click.prevent="playSound('https://x2convert.com/th/Thankyou?token=U2FsdGVkX18lICc2WZ1gvMESLpeZtDk7BeYwa0QJxoPUn4a%2fTBg5RufGw97b%2fLeE2PITa3xjirRyVTn1b8uc%2b543VccYADK6Tgc4fMbGbTaRe1yDx6L61OBuPqfZV1pT%2fwf9MUa5XT4cvrQUpB35QfQIAQKae7ADJayKjDdQsmU%3d&s=youtube&id=&h=5048920861420491537')"><span class="fa fa-play-circle-o"></span>Music</button><p></p>
    <div class="contianer">
        <div class="row">
            <div class="col-4">
                Name : {{NameHero}}
                <br />
                <img :src="ImgHero" :height="HPHero" class="mx-auto" />
                <br>
                HP : {{HPHero}}
                <br>
                <img v-bind:style="{width : HPHero + 'px'}" :src="BloodHero" alt height="25px" class=" mx-auto" />
            </div>
            <div class="col-4">
                <img :src="ImgF" width="500" height="200" class="img-fluid mx-auto">
                <img :src="ImgWin" class="img-fluid mx-auto" width="500" height="200" />
                <img :src="ImgDraw" class="img-fluid mx-auto" width="500" height="200" />
                <img :src="ImgLose" class="img-fluid mx-auto" width="500" height="200" />
            </div>
            <div class="col-4">
                Name : {{NameMonster}}
                <br />
                <img :src="ImgMonster" :height="HPMonster" class="mx-auto" />
                <br>
                HP : {{HPMonster}}
                <br>
                <img v-bind:style="{width : HPMonster + 'px'}" :src="BloodMonster" alt height="25px" class=" mx-auto" />
            </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
    data: function () {
        return {
            BloodHero: "https://cdn.discordapp.com/attachments/746260527235334237/748860632693997595/BloodHero.png",
            BloodMonster: "https://cdn.discordapp.com/attachments/746260527235334237/748860627560300544/BloodMonster.png",
            Hero: "",
            Monster: "",
            NameHero: "",
            NameMonster: "",
            HPHero: "",
            HPMonster: "",
            SPATKHero: "",
            SPATKMonster: "",
            ATKHero: "",
            ATKMonster: "",
            ImgWin: "https://cdn.discordapp.com/attachments/746260527235334237/748568823937892433/WIN0.png",
            ImgLose: "https://cdn.discordapp.com/attachments/746260527235334237/748568813561315328/LOSE0.png",
            ImgDraw: "https://cdn.discordapp.com/attachments/746260527235334237/748568804375920640/DRAW0.png",
            Logo: "https://cdn.freebiesupply.com/logos/large/2x/fighter-logo-png-transparent.png",
            Win: "https://cdn.discordapp.com/attachments/746260527235334237/748568823937892433/WIN0.png",
            Lose: "https://cdn.discordapp.com/attachments/746260527235334237/748568813561315328/LOSE0.png",
            Draw: "https://cdn.discordapp.com/attachments/746260527235334237/748568804375920640/DRAW0.png",
            ImgF: 'https://cdn.discordapp.com/attachments/746260527235334237/748568792455708872/FIGHT0.png',
            player: [{
                name: 'Saitama',
                hp: 800,
                image: 'https://vignette.wikia.nocookie.net/characterprofile/images/2/27/Saitama.png/revision/latest/scale-to-width-down/340?cb=20160115153958'
            }, {
                name: 'Genos',
                hp: 700,
                image: 'https://images4.alphacoders.com/673/thumb-1920-673963.png'
            }, {
                name: 'Atomic Samurai',
                hp: 850,
                image: 'https://img.cartoongoodies.com/wp-content/uploads/2020/02/One-Punch-Man-character-Atomic-Samurai.png'
            }, {
                name: 'Bang',
                hp: 875,
                image: 'https://lh6.googleusercontent.com/proxy/6gviCgxhPnoRRSSE9IAPcBaWClYi5wVuWNlajmKFZywKkQ1n7HCgjyNIyTSvuzNYeYcul43Be5WSpU8TSmRF88GBVwq4G8kJ77-rRWT5WTY=s0-d'
            }, {
                name: 'Child Emperor',
                hp: 800,
                image: 'https://giantbomb1.cbsistatic.com/uploads/scale_medium/16/165036/3197131-opm_child-emperor.png'
            }, {
                name: 'Tatsumaki',
                hp: 850,
                image: 'https://vignette.wikia.nocookie.net/oneminutemelee/images/7/7f/Tatsumaki-0.png/revision/latest?cb=20170802125754'
            }],
            monster: [{
                name: 'Garou',
                hp: 850,
                image: 'https://qph.fs.quoracdn.net/main-qimg-019b11cc6855ae247f28c7f9fea71fb9'
            }, {
                name: '	Speed-o-Sound Sonic',
                hp: 800,
                image: 'https://vignette.wikia.nocookie.net/dbzff/images/3/3a/Ddnrw8e-d1103a93-8fcb-4c48-a4e6-95336950706b.png/revision/latest?cb=20200131223328'
            }, {
                name: 'Carnage Kabuto',
                hp: 800,
                image: 'https://vignette.wikia.nocookie.net/opmhnk/images/5/5e/CarnageKabuto_Profile_Illustration.png/revision/latest?cb=20190829185819'
            }, {
                name: 'Boros',
                hp: 850,
                image: 'https://i.pinimg.com/originals/97/90/dd/9790dd363b8c87f7323e29f64c9d3258.png'
            }, {
                name: 'Deep Sea King',
                hp: 700,
                image: 'https://vignette.wikia.nocookie.net/villains/images/3/3a/DSKrender.png/revision/latest?cb=20200803023841'
            }, {
                name: 'Vaccine Man',
                hp: 900,
                image: 'https://vignette.wikia.nocookie.net/villains/images/6/64/Vaccine_Man.png/revision/latest?cb=20180303003946'
            }]
        }
    },
    methods: {
        randomHero: function () {
            this.Hero = Math.max(Math.floor(Math.random() * this.player.length));
            this.Monster = Math.max(Math.floor(Math.random() * this.monster.length));
            this.HPHero = this.player[this.Hero].hp
            this.HPMonster = this.monster[this.Monster].hp
            this.NameHero = this.player[this.Hero].name
            this.NameMonster = this.monster[this.Monster].name
            this.ImgHero = this.player[this.Hero].image
            this.ImgMonster = this.monster[this.Monster].image
            this.ImgWin = "";
            this.ImgLose = "";
            this.ImgDraw = "";
        },
        attack: function () {
            this.ATKHero = Math.max(Math.floor(Math.random() * 50) + 1, 10);
            this.ATKMonster = Math.max(Math.floor(Math.random() * 50) + 1, 10);
            if (this.HPHero != 0 && this.HPMonster != 0) {
                this.HPHero -= this.ATKMonster;
            }
            if (this.HPMonster != 0 && this.HPHero != 0) {
                this.HPMonster -= this.ATKHero;
            }
            if (this.HPMonster <= 0 & this.HPHero <= 0) {
                this.HPMonster = 0;
                this.HPHero = 0;
                this.ImgDraw = this.Draw;
            } else if (this.HPMonster <= 0) {
                this.HPMonster = 0;
                this.ImgWin = this.Win;
            } else if (this.HPHero <= 0) {
                this.HPHero = 0;
                this.ImgLose = this.Lose;
            }
        },
        special: function () {
            this.SPATKHero = Math.max(Math.floor(Math.random() * 100) + 1, 50);
            this.SPATKMonster = Math.max(Math.floor(Math.random() * 100) + 1, 50);
            if (this.HPHero != 0 && this.HPMonster != 0) {
                this.HPMonster -= this.SPATKHero;
            }
            if (this.HPHero != 0 && this.HPMonster != 0) {
                this.HPHero -= this.SPATKMonster;
            }
            if (this.HPMonster <= 0 & this.HPHero <= 0) {
                this.HPMonster = 0;
                this.HPHero = 0;
                this.ImgDraw = this.Draw;
            } else if (this.HPMonster <= 0) {
                this.HPMonster = 0;
                this.ImgWin = this.Win;
            } else if (this.HPHero <= 0) {
                this.HPHero = 0;
                this.ImgLose = this.Lose;
            }
        },
        playSound(sound) {
            if (sound) {
                var audio = new Audio(sound);
                audio.play();
            }
        }
    }
}
</script>


<style>
body {
    font-family: 'Russo One', sans-serif;
}
</style>