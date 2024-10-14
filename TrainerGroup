import java.time.LocalTime;
import java.util.HashSet;
import java.util.Set;

public class TrainerGroup {
    private Set<String> allowedIPs;
    private Set<String> trainers;
    private LocalTime startNightTime = LocalTime.of(22, 0);
    private LocalTime endNightTime = LocalTime.of(6, 0);

    public TrainerGroup() {
        this.allowedIPs = new HashSet<>();
        this.trainers = new HashSet<>();
    }

    public void allowIP(String ip) {
        allowedIPs.add(ip);
    }

    public void addTrainer(String trainerId) {
        trainers.add(trainerId);
    }

    public boolean isIPAllowed(String ip) {
        return allowedIPs.contains(ip);
    }

    public boolean isTrainer(String trainerId) {
        return trainers.contains(trainerId);
    }

    private boolean isNightTime() {
        LocalTime now = LocalTime.now();
        return (now.isAfter(startNightTime) || now.isBefore(endNightTime));
    }

    public boolean canDownloadVideo(String trainerId, String ip) {
        if (isTrainer(trainerId) && isIPAllowed(ip)) {
            if (isNightTime()) {
                System.out.println("Trainer " + trainerId + " não pode baixar vídeos à noite.");
                return false;
            }
            return true;
        }
        System.out.println("Acesso negado para o trainer " + trainerId + " com IP " + ip);
        return false;
    }
}
