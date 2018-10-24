import java.util.Random;
import java.util.Scanner;

    public class main {

        public static void main(String[] args) {


            boolean oj;
            boolean atack;
            boolean shild;

            //int AltairMerser = 1000;
            //int DarkReaper = 600;
            //int Dragon = 300;
            int DarkKnight = 650;
            int Troll = 800;
            int Goblin = 200;
            int RadGoblin = 250;

            int dangeon = 0;
            int village = 0;
            int DarkForest = 0;

            int Player = 100;

            int zelye = 5;
            int magic = 100;

            int Progress = 0;
            int DangeonProgress = 0;
            int DarkForestProgress = 0;
            int VillageProgress = 0;

            Scanner scan = new Scanner(System.in);
            Random random = new Random();
            System.out.println("Битва с Гоблином");

            if (Goblin == 200) {
                System.out.println("Выберите класс ");
                System.out.println("От этого зависят характеристики главного героя, тобиш вас) ");
                System.out.println("1 - Рыцарь, 2 - Чародей, 3 - Знахарь");
                int number = scan.nextInt();
                if (number == 1) {
                    Player = Player + 100;
                    magic = magic - 50;
                }
                if (number == 2) {
                    magic = magic + 100;
                    Player = Player - 25;
                }
                if (number == 3) {
                    zelye = zelye + 15;
                    Player = Player - 50;
                }
            }

            if (Goblin > 150) {
                System.out.println("Выберите снаряжение");
                System.out.println("1 - Сумка с целебными зельями (больше зелий), 2 - Чародейский плащ (больше магии), 3 - Латная броня (больше здоровья)");
                int number = scan.nextInt();
                if (number == 1) {
                    zelye = zelye + 5;
                }
                if (number == 2) {
                    magic = magic + 100;
                }
                if (number == 3) {
                    Player = Player + 100;
                }
            }
            System.out.println("У вас четыре действия: 1- атака, 2 - закрыться шитоом, 3 - выпить зелье(их всего 4), 4 - слабое атакующее заклинание (15 маны), 5 - мощное атакующее заклинание (45 маны)");
            System.out.println("Прежде чем вы начнете свой бой, обратите свое внимание на эту надпись:");
            System.out.println("У вас ограниченное количество очков жизней, очков маны, а также зелий");
            System.out.println("Потерянные очки жизней можно восполнить зельями ( + 50), а потраченные очки маны восполняются сами во время атаки или защиты");
            System.out.println("В начале пути у вас будет 5 ( 10 +/-) Зелий, 100 ( 200 +/-) Очков жизни, 100 ( 200 +/-) Очков маны");
            System.out.println("( В зависимости от того что вы выбрали в начале игры )");
            System.out.println("Слабое атакующее заклинание требует 15 очков маны, а мощное атакующее заклинание требует 45 очков маны ");
            System.out.println("Битва начинается!");


            while (Player > 0) {

                if (Player > 0) {

                    //Гоблин

                    if (dangeon == 0) {

                        System.out.println("Битва с гоблином");

                        while (Goblin > 0) {
                            System.out.println("Ваш Ход, выберите действие");
                            int number = scan.nextInt();
                            if (number == 1) {
                                atack = random.nextBoolean();
                                if (atack == true) {
                                    Goblin = Goblin - (1 + (int) (Math.random() * 45));
                                    System.out.println("Осталось нанести урона:" + Goblin);
                                    Player = Player - (1 + ((int) (Math.random() * 35)));
                                    if (magic < 100) {
                                        magic = magic + 5;
                                    }
                                    System.out.println("Ваш уровень здоровья:" + Player);
                                    System.out.println("Ваш уровень маны" + magic);
                                    System.out.println("Количество зелий :" + zelye);
                                } else {
                                    System.out.println("Промах");
                                    Player = Player - (1 + ((int) (Math.random() * 50)));
                                    System.out.println("Ваш уровень здоровья:" + Player);
                                }
                            } else {
                                if (number == 3) {
                                    if (zelye >= 1) {
                                        if (Player < 150) {
                                            Player = Player + 50;
                                            zelye = zelye - 1;
                                            Player = Player - (1 + ((int) (Math.random() * 5)));
                                            System.out.println("Ваш уровень здоровья:" + Player);
                                            System.out.println("Количество зелий :" + zelye);
                                        } else {
                                            System.out.println("Зелья кончились(");
                                            System.out.println("Ваш уровень здоровья:" + Player);
                                            System.out.println("Ваш уровень маны" + magic);
                                        }
                                    }
                                }
                            }

                            if (number == 2) {
                                shild = random.nextBoolean();
                                if (shild == true) {
                                    System.out.println("Вы заблокировали удар");
                                    if (magic < 100) {
                                        magic = magic + 5;
                                    }
                                    System.out.println("Ваш уровень маны" + magic);
                                    System.out.println("Количество зелий :" + zelye);
                                } else {
                                    Player = Player - (1 + ((int) (Math.random() * 60)) / 3);

                                    System.out.println("Вы частично заблокировали удар");
                                    System.out.println("Ваш уровень здоровья:" + Player);
                                    System.out.println("Количество зелий :" + zelye);
                                }
                            }
                            if (number == 5) {
                                oj = random.nextBoolean();
                                if (oj == true) {
                                    if (magic >= 45) {
                                        magic = magic - 45;
                                        Goblin = Goblin - (1 + (int) (Math.random() * 75));
                                        System.out.println("Осталось нанести урона:" + Goblin);
                                        System.out.println("Ваш уровень маны" + magic);
                                        System.out.println("Ваш уровень здоровья:" + Player);
                                        System.out.println("Количество зелий :" + zelye);
                                    }
                                    if (magic < 45) {
                                        System.out.println("Мана кончилась(");
                                    }
                                } else {
                                    System.out.println("Промах");
                                    magic = magic - 45;
                                    System.out.println("Ваш уровень маны" + magic);
                                    Player = Player - (1 + ((int) (Math.random() * 30)));
                                    System.out.println("Ваш уровень здоровья:" + Player);
                                    System.out.println("Количество зелий :" + zelye);
                                }
                            }

                            if (number == 4) {
                                oj = random.nextBoolean();
                                if (oj == true) {
                                    if (magic >= 15) {
                                        magic = magic - 15;
                                        Goblin = Goblin - (1 + (int) (Math.random() * 25));
                                        System.out.println("Осталось нанести урона:" + Goblin);
                                        System.out.println("Ваш уровень здоровья:" + Player);
                                        System.out.println("Ваш уровень маны" + magic);
                                        System.out.println("Количество зелий :" + zelye);
                                    }
                                    if (magic < 15) {
                                        System.out.println("Мана закончилась");
                                    }
                                } else {
                                    Player = Player - (1 + ((int) (Math.random() * 30)));
                                    System.out.println("Промах");
                                    System.out.println("Ваш уровень здоровья:" + Player);
                                    System.out.println("Ваш уровень маны" + magic);
                                    System.out.println("Количество зелий :" + zelye);
                                }
                            }
                            if (Goblin < 0) {
                                dangeon = dangeon + 1;
                            }
                            if (Player < 0) {
                                break;
                            }
                        }

                        if (Goblin <= 0) {
                            System.out.println("Гоблин повержен!");
                            System.out.println("Вы забрали голову гоблина как трофей");
                            System.out.println("Выберите предмет в логове гоблина :");
                            System.out.println(" 1 - Кольцо жизненной силы, 2 - Броня гоблина, 3 - Амулет из магическй руны ");
                            int number = scan.nextInt();
                            if (number == 1) {
                                Player = Player + 50;
                                zelye = zelye + 10;
                            }
                            if (number == 2) {
                                Player = Player + 250;
                            }
                            if (number == 3) {
                                magic = magic + 250;
                            }
                        }
                    }

                    //Радиоационный Гоблин
                    if (dangeon == 1) {

                        System.out.println("Битва с РадГоблином");

                        while (RadGoblin > 0) {
                            System.out.println("Ваш Ход, выберите действие");
                            int number = scan.nextInt();
                            if (number == 1) {
                                atack = random.nextBoolean();
                                if (atack == true) {
                                    RadGoblin = RadGoblin - (1 + (int) (Math.random() * 55));
                                    System.out.println("Осталось нанести урона:" + RadGoblin);
                                    Player = Player - (1 + ((int) (Math.random() * 30)));
                                    if (magic < 100) {
                                        magic = magic + 5;
                                    }
                                    System.out.println("Ваш уровень здоровья:" + Player);
                                    System.out.println("Ваш уровень маны" + magic);
                                    System.out.println("Количество зелий :" + zelye);
                                } else {
                                    System.out.println("Промах");
                                    Player = Player - (1 + ((int) (Math.random() * 40)));
                                    System.out.println("Ваш уровень здоровья:" + Player);
                                }
                            } else {
                                if (number == 3) {
                                    if (zelye >= 1) {
                                        if (Player < 150) {
                                            Player = Player + 50;
                                            zelye = zelye - 1;
                                            Player = Player - (1 + ((int) (Math.random() * 6)));
                                            System.out.println("Ваш уровень здоровья:" + Player);
                                            System.out.println("Количество зелий :" + zelye);
                                        } else {
                                            //System.out.println("Зелья кончились(");
                                            //System.out.println("Ваш уровень здоровья:" + Player);
                                            //System.out.println("Ваш уровень маны" + magic);
                                        }
                                    }
                                }
                            }


                            if (number == 2) {
                                shild = random.nextBoolean();
                                if (shild == true) {
                                    System.out.println("Вы заблокировали удар");
                                    if (magic < 100) {
                                        magic = magic + 5;
                                    }
                                    System.out.println("Ваш уровень маны" + magic);
                                    System.out.println("Количество зелий :" + zelye);
                                } else {
                                    Player = Player - (1 + ((int) (Math.random() * 50)) / 3);

                                    System.out.println("Вы частично заблокировали удар");
                                    System.out.println("Ваш уровень здоровья:" + Player);
                                    System.out.println("Количество зелий :" + zelye);
                                }
                            }
                            if (number == 5) {
                                oj = random.nextBoolean();
                                if (oj == true) {
                                    if (magic >= 45) {
                                        magic = magic - 45;
                                        RadGoblin = RadGoblin - (1 + (int) (Math.random() * 80));
                                        System.out.println("Осталось нанести урона:" + RadGoblin);
                                        System.out.println("Ваш уровень маны" + magic);
                                        System.out.println("Ваш уровень здоровья:" + Player);
                                        System.out.println("Количество зелий :" + zelye);
                                    }
                                    if (magic < 45) {
                                        System.out.println("Мана кончилась(");
                                    }
                                } else {
                                    System.out.println("Промах");
                                    magic = magic - 45;
                                    System.out.println("Ваш уровень маны" + magic);
                                    Player = Player - (1 + ((int) (Math.random() * 25)));
                                    System.out.println("Ваш уровень здоровья:" + Player);
                                    System.out.println("Количество зелий :" + zelye);
                                }
                            }

                            if (number == 4) {
                                oj = random.nextBoolean();
                                if (oj == true) {
                                    if (magic >= 15) {
                                        magic = magic - 15;
                                        RadGoblin = RadGoblin - (1 + (int) (Math.random() * 35));
                                        System.out.println("Осталось нанести урона:" + RadGoblin);
                                        System.out.println("Ваш уровень здоровья:" + Player);
                                        System.out.println("Ваш уровень маны" + magic);
                                        System.out.println("Количество зелий :" + zelye);
                                    }
                                    if (magic < 15) {
                                        System.out.println("Мана закончилась");
                                    }
                                } else {
                                    Player = Player - (1 + ((int) (Math.random() * 28)));
                                    System.out.println("Промах");
                                    System.out.println("Ваш уровень здоровья:" + Player);
                                    System.out.println("Ваш уровень маны" + magic);
                                    System.out.println("Количество зелий :" + zelye);
                                }
                            }
                            if (RadGoblin < 0) {
                                dangeon = dangeon + 1;
                                Progress = Progress + 1;
                                DangeonProgress = DangeonProgress + 1;
                            }
                            if (Player < 0) {
                                break;
                            }
                        }
                        if (RadGoblin <= 0) {
                            System.out.println("РадиоационныйГоблин повержен!");
                            System.out.println("");
                            System.out.println("К сожалению вы не придумали что делать с его умершим телом,");
                            System.out.println("поэтому вы решили проверить его карманы ни лежит ли чего лишнего в них : ");
                            System.out.println("вы нашли : эликсир здоровья, эликсир маны, ");
                            System.out.println("");
                            System.out.println("видимо вы убили какого-то важного гоблина... ");
                            System.out.println("");
                            System.out.println("Выберите предмет в логове гоблина :");
                            System.out.println(" 1 - , 2 - , 3 -  ");
                            int number = scan.nextInt();
                            if (number == 1) {
                                Player = Player + 50;
                                zelye = zelye + 10;
                            }
                            if (number == 2) {
                                Player = Player + 250;
                            }
                            if (number == 3) {
                                magic = magic + 250;
                            }
                        }
                        Goblin = Goblin + 200;
                        RadGoblin = RadGoblin + 250;

                        if (Progress == 1) {
                            if (village == 0) {
                                System.out.println("Вы за зачистили пещеру. И увидели выход из нее");
                                System.out.println("Куда вы хотите направиться?");
                                System.out.println(" 1 - В деревню, 2 - На окраину деревни, 3 - Снова отправиться в пещеру на поиски приключений ");
                                System.out.println("текущее значение данжона" + dangeon);
                                int number = scan.nextInt();
                                if (number == 1) {
                                    village = village + 1;
                                }

                                if (number == 2) {
                                    village = village + 2;
                                }
                                if (number == 3) {
                                    dangeon = dangeon - 2;
                                }
                            }
                        }
                    }
                    ////
                    //Деревня
                    //

                    if (village == 1) {
                        System.out.println("Вот вы и дошли до ближайшей деревушки  ");
                        System.out.println(" Мышьяково ");
                        System.out.println(" ");
                        System.out.println(" 1 - Здесь можно отдохнуть и пополнить силы, 2 - Также можно сходить в магазин, 3 - Отправиться к окраине деревни, 4 - Или же отправиться в пещеру");
                        System.out.println(" 5 - Ну а если у вас стальные яйца то вполне можно отправиться в темный лес ");
                        village = village - 1;
                        Progress = Progress - 1;
                        if (village > 0) {
                            village = village--;
                        }
                        int number = scan.nextInt();
                        if (number == 1) {
                            village = village + 1;
                        }

                        if (number == 2) {
                            village = village + 2;
                        }

                        if (number == 3) {
                            village = village + 2;
                        }

                        if (number == 4) {
                            dangeon = dangeon - 2;
                        }
                        if (number == 5) {
                            DarkForest = DarkForest + 1;
                        }
                    }


                    //Троль
                    if (village == 2) {
                        System.out.println("Ваш следующий противник Троль");
                        System.out.println("текущее значение данжона" + dangeon);
                        while (Troll > 0) {
                            System.out.println("Ваш Ход, выберите действие");
                            int number = scan.nextInt();
                            if (number == 1) {
                                atack = random.nextBoolean();
                                if (atack == true) {
                                    Troll = Troll - (1 + (int) (Math.random() * 55));
                                    System.out.println("Осталось нанести урона:" + Troll);
                                    Player = Player - (1 + ((int) (Math.random() * 10)));
                                    if (magic < 100) {
                                        magic = magic + 10;
                                    }
                                    System.out.println("Ваш уровень здоровья:" + Player);
                                    System.out.println("Ваш уровень маны" + magic);
                                    System.out.println("Количество зелий :" + zelye);
                                } else {
                                    System.out.println("Промах");
                                    Player = Player - (1 + ((int) (Math.random() * 40)));
                                    System.out.println("Ваш уровень здоровья:" + Player);
                                    magic = magic + 10;
                                }
                            }

                            if (number == 3) {
                                if (zelye >= 1) {
                                    if (Player < 150) {
                                        Player = Player + 50;
                                        zelye = zelye - 1;
                                        Player = Player - (1 + ((int) (Math.random() * 3)));
                                        System.out.println("Ваш уровень здоровья:" + Player);
                                        System.out.println("Количество зелий :" + zelye);
                                    } else {
                                        System.out.println("Зелья кончились(");
                                        System.out.println("Ваш уровень здоровья:" + Player);
                                        System.out.println("Ваш уровень маны" + magic);
                                    }
                                }
                            }

                            if (number == 2) {
                                shild = random.nextBoolean();
                                if (shild == true) {
                                    System.out.println("Вы заблокировали удар");
                                    if (magic < 100) {
                                        magic = magic + 15;
                                    }
                                    System.out.println("Ваш уровень маны" + magic);
                                    System.out.println("Количество зелий :" + zelye);
                                } else {
                                    Player = Player - (1 + ((int) (Math.random() * 40)) / 3);
                                    magic = magic + 5;
                                    System.out.println("Вы частично заблокировали удар");
                                    System.out.println("Ваш уровень здоровья:" + Player);
                                    System.out.println("Количество зелий :" + zelye);
                                }
                            }
                            if (number == 5) {
                                oj = random.nextBoolean();
                                if (oj == true) {
                                    if (magic >= 45) {
                                        magic = magic - 45;
                                        Troll = Troll - (1 + (int) (Math.random() * 95));
                                        System.out.println("Осталось нанести урона:" + Troll);
                                        System.out.println("Ваш уровень маны" + magic);
                                        System.out.println("Ваш уровень здоровья:" + Player);
                                        System.out.println("Количество зелий :" + zelye);
                                    }
                                    if (magic < 45) {
                                        System.out.println("Мана кончилась(");
                                    }
                                } else {
                                    System.out.println("Промах");
                                    magic = magic - 45;
                                    System.out.println("Ваш уровень маны" + magic);
                                    Player = Player - (1 + ((int) (Math.random() * 20)));
                                    System.out.println("Ваш уровень здоровья:" + Player);
                                    System.out.println("Количество зелий :" + zelye);
                                }
                            }

                            if (number == 4) {
                                oj = random.nextBoolean();
                                if (oj == true) {
                                    if (magic >= 15) {
                                        magic = magic - 15;
                                        Troll = Troll - (1 + (int) (Math.random() * 45));
                                        System.out.println("Осталось нанести урона:" + Troll);
                                        System.out.println("Ваш уровень здоровья:" + Player);
                                        System.out.println("Ваш уровень маны" + magic);
                                        System.out.println("Количество зелий :" + zelye);
                                    }
                                    if (magic < 15) {
                                        System.out.println("Мана закончилась");
                                    }
                                } else {
                                    Player = Player - (1 + ((int) (Math.random() * 20)));
                                    System.out.println("Промах");
                                    System.out.println("Ваш уровень здоровья:" + Player);
                                    System.out.println("Ваш уровень маны" + magic);
                                    System.out.println("Количество зелий :" + zelye);
                                }
                            }

                            magic = magic + 15;
                            Player = Player + 10;

                            if (Troll <= 0) {
                                Progress = Progress + 1;
                                village = village + 1;
                            }
                            if (Player < 0) {
                                break;
                            }
                        }
                    }

                    if (Troll <= 0) {
                        Troll = Troll + 800;
                    }


                    //Деревня (После тролля)

                    if (Progress == 1) {
                        if (village == 3) {
                            System.out.println("Пускай вы и облазили все эти чертовы окраины, но все же, вы это сделали))");
                            System.out.println("Куда вы хотите направиться?");
                            System.out.println(" 1 - В деревню, 2 - Отправиться в пещеру на поиски приключений, 3 - Отправиться в Темный Лес  ");
                            int number = scan.nextInt();
                            if (number == 1) {
                                village = village - 2;
                            }

                            if (number == 2) {
                                dangeon = dangeon - 2;
                            }

                            if (number == 3) {
                                DarkForest = DarkForest + 1;
                            }
                        }
                    }


                    if (DarkForest == 1) {

                        //Темный Рыцарь

                        System.out.println("Ваш противник Темный Рыцарь");
                        while (DarkKnight > 0) {
                            System.out.println("Ваш Ход, выберите действие");
                            int number = scan.nextInt();
                            if (number == 1) {
                                atack = random.nextBoolean();
                                if (atack == true) {
                                    DarkKnight = DarkKnight - (1 + (int) (Math.random() * 55));
                                    System.out.println("Осталось нанести урона:" + DarkKnight);
                                    Player = Player - (1 + ((int) (Math.random() * 25)));
                                    if (magic < 100) {
                                        magic = magic + 5;
                                    }
                                    System.out.println("Ваш уровень здоровья:" + Player);
                                    System.out.println("Ваш уровень маны" + magic);
                                    System.out.println("Количество зелий :" + zelye);
                                } else {
                                    System.out.println("Промах");
                                    Player = Player - (1 + ((int) (Math.random() * 60)));
                                    System.out.println("Ваш уровень здоровья:" + Player);
                                }
                            }
                            //else {
                            if (number == 3) {
                                if (zelye >= 1) {
                                    if (Player < 150) {
                                        Player = Player + 50;
                                        zelye = zelye - 1;
                                        Player = Player - (1 + ((int) (Math.random() * 10)));
                                        System.out.println("Ваш уровень здоровья:" + Player);
                                        System.out.println("Количество зелий :" + zelye);
                                    } else {
                                        System.out.println("Зелья кончились(");
                                        System.out.println("Ваш уровень здоровья:" + Player);
                                        System.out.println("Ваш уровень маны" + magic);
                                    }
                                }
                            }
                            //}

                            if (number == 2) {
                                shild = random.nextBoolean();
                                if (shild == true) {
                                    System.out.println("Вы заблокировали удар");
                                    if (magic < 100) {
                                        magic = magic + 10;
                                    }
                                    System.out.println("Ваш уровень маны" + magic);
                                    System.out.println("Количество зелий :" + zelye);
                                } else {
                                    Player = Player - (1 + ((int) (Math.random() * 50)) / 3);

                                    System.out.println("Вы частично заблокировали удар");
                                    System.out.println("Ваш уровень здоровья:" + Player);
                                    System.out.println("Количество зелий :" + zelye);
                                }
                            }
                            if (number == 5) {
                                oj = random.nextBoolean();
                                if (oj == true) {
                                    if (magic >= 45) {
                                        magic = magic - 45;
                                        DarkKnight = DarkKnight - (1 + (int) (Math.random() * 85));
                                        System.out.println("Осталось нанести урона:" + DarkKnight);
                                        System.out.println("Ваш уровень маны" + magic);
                                        System.out.println("Ваш уровень здоровья:" + Player);
                                        System.out.println("Количество зелий :" + zelye);
                                    }
                                    if (magic < 45) {
                                        System.out.println("Мана кончилась(");
                                    }
                                } else {
                                    System.out.println("Промах");
                                    magic = magic - 45;
                                    System.out.println("Ваш уровень маны" + magic);
                                    Player = Player - (1 + ((int) (Math.random() * 40)));
                                    System.out.println("Ваш уровень здоровья:" + Player);
                                    System.out.println("Количество зелий :" + zelye);
                                }
                            }

                            if (number == 4) {
                                oj = random.nextBoolean();
                                if (oj == true) {
                                    if (magic >= 15) {
                                        magic = magic - 15;
                                        DarkKnight = DarkKnight - (1 + (int) (Math.random() * 30));
                                        System.out.println("Осталось нанести урона:" + Troll);
                                        System.out.println("Ваш уровень здоровья:" + Player);
                                        System.out.println("Ваш уровень маны" + magic);
                                        System.out.println("Количество зелий :" + zelye);
                                    }
                                    if (magic < 15) {
                                        System.out.println("Мана закончилась");
                                    }
                                } else {
                                    Player = Player - (1 + ((int) (Math.random() * 60)));
                                    System.out.println("Промах");
                                    System.out.println("Ваш уровень здоровья:" + Player);
                                    System.out.println("Ваш уровень маны" + magic);
                                    System.out.println("Количество зелий :" + zelye);
                                }
                            }

                            if (DarkKnight < 0) {
                                break;
                            }
                            if (Player < 0) {
                                break;
                            }
                        }
                        DarkForest = DarkForest - 1;
                    }


                    System.out.println("Ход Противника");
                    magic = magic + 5;
                    Player = Player + 5;


                    if (Player < 0) {
                        System.out.println("Противник выйграл!");
                        break;
                    }

                    if (Goblin < 0) {
                        if (Troll < 0) {
                            if (DarkKnight < 0) {
                                System.out.println("Вы победили");
                                break;
                            }
                        }
                    }
                }
            }
        }
    }
