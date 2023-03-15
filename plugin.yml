package com.example.explodeplugin;

import org.bukkit.Location;
import org.bukkit.Material;
import org.bukkit.entity.Player;
import org.bukkit.event.EventHandler;
import org.bukkit.event.Listener;
import org.bukkit.event.player.PlayerInteractEvent;
import org.bukkit.plugin.java.JavaPlugin;

public class ExplodePlugin extends JavaPlugin implements Listener {
    @Override
    public void onEnable() {
        // Регистрируем события для плагина
        getServer().getPluginManager().registerEvents(this, this);
    }

    @EventHandler
    public void onPlayerInteract(PlayerInteractEvent event) {
        Player player = event.getPlayer();

        // Проверяем, имеет ли игрок право на взрывы
        if (player.hasPermission("explodeplugin.explode")) {
            // Получаем местоположение игрока
            Location loc = player.getLocation();

            // Взрываем блоки в радиусе 10 блоков
            loc.getWorld().createExplosion(loc, 10f, true, false);

            // Разрушаем блоки в радиусе 10 блоков
            for (int x = -10; x <= 10; x++) {
                for (int y = -10; y <= 10; y++) {
                    for (int z = -10; z <= 10; z++) {
                        Location blockLoc = loc.clone().add(x, y, z);

                        if (blockLoc.getBlock().getType() != Material.AIR) {
                            blockLoc.getBlock().breakNaturally();
                        }
                    }
                }
            }
        }
    }
}
