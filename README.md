private static String championName = "Ezreal";
        private static Obj_AI_Hero Player;
        private static Menu Menu;
        private static OrbwalkingOrbwalker orbwalker;
        private static Spell Q, W, E, R;
        0 References
        static void Main(string[] args)
        {
            CustomEvents.Game.OnGameLoad += Game_OnGameLoad;
        }
    }
}

1 reference
static void Game_OnGameLoad(EventArgs args)
{
       Player = ObjectManager.Player;
       if (Player.ChampionName != championName)
       {
           return;
       }
       //When the assembly is injected and the game is loaded,this will get called
       _menu = new Menu("Tutorial Ezreal","tutorial.ezreal",true);
       var orbwalkerMenu = new Menu("Orbwalker","tutorial.ezreal.orbwalker");
       _orbwalker = new Orbwalking.Orbwalker(orbwalkerMenu);
       
       _menu.AddSubMenu(orbwalkerMenu);
      
       TargetSelector.AddToMenu(_menu);
       
       var comboMenu = new Menu("Combo", "tutorial.ezreal.combo");
       { 
            comboMenu.AddItem(new MenuItem("tutorial.ezreal.combo.useq", "Use Q").SetValue(true));
            comboMenu.AddItem(new MenuItem("tutorial.ezreal.combo.usew", "Use W").SetValue(true));
            comboMenu.AddItem(new MenuItem("tutorial.ezreal.combo.usee", "Use E").SetValue(true));
            comboMenu.AddItem(new MenuItem("tutorial.ezreal.combo.user", "Use R").SetValue(true));
       }
       _menu.AddSubMenu(comboMenu);
       
       var  harrassMenu = new Menu("Harrass","tutorial.ezreal.harrass");
       {
            harrasMenu.AddItem(new MenuItem("tutorial.ezreal.harrass.useq","Use Q").SetValue(true));
            harrasMenu.AddItem(new MenuItem("tutorial.ezreal.harrass.usew","Use W").SetValue(true));
            harrasMenu.AddItem(new MenuItem("tutorial.ezreal.harrass.usee","Use E").SetValue(true));
            harrasMenu.AddItem(new MenuItem("tutorial.ezreal.harrass.user","Use R").SetValue(true));
       }
       _menu.AddSubMenu(harrassMenu);

       _menu.AddToMainMenu();
       }
