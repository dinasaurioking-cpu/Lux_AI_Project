
# Lux_AI_Project

class RexLogoPainter extends CustomPainter {
  @override
  void paint(Canvas canvas, Size size) {
    final paint = Paint()
      ..color = Colors.blueAccent
      ..style = PaintingStyle.fill;

    final strokePaint = Paint()
      ..color = Colors.white
      ..style = PaintingStyle.stroke
      ..strokeWidth = 6;

    final path = Path();

    // Cuerpo principal (más dinámico)
    path.moveTo(size.width * 0.15, size.height * 0.55);   // cola base
    path.quadraticBezierTo(size.width * 0.05, size.height * 0.65,
                           size.width * 0.18, size.height * 0.75); // cola curva

    // Cuerpo y espalda
    path.lineTo(size.width * 0.28, size.height * 0.72);
    path.lineTo(size.width * 0.35, size.height * 0.35);   // cabeza sube
    path.lineTo(size.width * 0.68, size.height * 0.32);   // frente
    path.lineTo(size.width * 0.82, size.height * 0.48);   // hocico
    path.lineTo(size.width * 0.75, size.height * 0.68);
    path.lineTo(size.width * 0.65, size.height * 0.78);
    path.lineTo(size.width * 0.32, size.height * 0.78);
    path.close();

    canvas.drawPath(path, paint);
    canvas.drawPath(path, strokePaint);

    // Ojo brillante (con toque de luz)
    final eyePaint = Paint()..color = Colors.white;
    canvas.drawCircle(Offset(size.width * 0.72, size.height * 0.48), 12, eyePaint);
    canvas.drawCircle(Offset(size.width * 0.735, size.height * 0.475), 6, Paint()..color = Colors.black);

    // Brillo en el ojo (efecto Lux)
    canvas.drawCircle(Offset(size.width * 0.725, size.height * 0.46), 3, Paint()..color = Colors.cyanAccent);

    // Patas fuertes
    canvas.drawRect(Rect.fromLTWH(size.width * 0.38, size.height * 0.75, 18, 35), paint);
    canvas.drawRect(Rect.fromLTWH(size.width * 0.62, size.height * 0.75, 18, 35), paint);

    // Espinas dorsales (estilo jurásico pero moderno)
    final spikePaint = Paint()..color = Colors.blue.shade900;
    for (double x = 0.38; x < 0.68; x += 0.08) {
      final pathSpike = Path();
      pathSpike.moveTo(size.width * x, size.height * 0.35);
      pathSpike.lineTo(size.width * (x - 0.03), size.height * 0.22);
      pathSpike.lineTo(size.width * (x + 0.03), size.height * 0.22);
      pathSpike.close();
      canvas.drawPath(pathSpike, spikePaint);
    }

    // Toque de "luz" (Lux) - pequeño glow en la cabeza
    final glowPaint = Paint()
      ..color = Colors.cyan.withOpacity(0.4)
      ..maskFilter = MaskFilter.blur(BlurStyle.normal, 12);
    canvas.drawCircle(Offset(size.width * 0.75, size.height * 0.40), 28, glowPaint);
  }

  @override
  bool shouldRepaint(CustomPainter oldDelegate) => false;
}Colors.blacksize.widthPaintingStyle.strokeColors.blueAccent// Ejemplo de uso
class LuxRexLogo extends StatelessWidget {
  final double size;

  const LuxRexLogo({super.key, this.size = 200});

  @override
  Widget build(BuildContext context) {
    return SizedBox(
      width: size,
      height: size,
      child: CustomPaint(
        painter: RexLogoPainter(),
      ),
    );
  }
}
import 'package:flutter/material.dart';

class RexLogoPainter extends CustomPainter {
  @override
  void paint(Canvas canvas, Size size) {
    // Paint principal - Cuerpo del Rex (Estilo limpio)
    final paint = Paint()
      ..color = Colors.blueAccent
      ..style = PaintingStyle.fill;

    // Paint para contornos (Borde blanco, estilo iOS)
    final strokePaint = Paint()
      ..color = Colors.white
      ..style = PaintingStyle.stroke
      ..strokeWidth = size.width * 0.015; // Escalable

    final path = Path();

    // --- Cuerpo y Silueta ---
    // Cola
    path.moveTo(size.width * 0.15, size.height * 0.55);
    path.quadraticBezierTo(
      size.width * 0.05, size.height * 0.65,
      size.width * 0.18, size.height * 0.75,
    );

    // Base del cuerpo y espalda
    path.lineTo(size.width * 0.28, size.height * 0.72);
    path.lineTo(size.width * 0.35, size.height * 0.35); // Cuello
    path.lineTo(size.width * 0.68, size.height * 0.32); // Frente
    path.lineTo(size.width * 0.82, size.height * 0.48); // Hocico
    path.lineTo(size.width * 0.75, size.height * 0.68);
    path.lineTo(size.width * 0.65, size.height * 0.78);
    path.lineTo(size.width * 0.32, size.height * 0.78);
    path.close();

    canvas.drawPath(path, paint);
    canvas.drawPath(path, strokePaint);

    // --- Ojo Inteligente (Híbrido) ---
    final eyeRadius = size.width * 0.03;
    final pupilRadius = eyeRadius * 0.5;
    final glowRadius = eyeRadius * 0.25;

    // Blanco del ojo
    final eyePaint = Paint()..color = Colors.white;
    canvas.drawCircle(
      Offset(size.width * 0.72, size.height * 0.48),
      eyeRadius,
      eyePaint,
    );

    // Pupila
    canvas.drawCircle(
      Offset(size.width * 0.735, size.height * 0.475),
      pupilRadius,
      Paint()..color = Colors.black,
    );

    // Brillo "Lux" (El toque de luz característico)
    canvas.drawCircle(
      Offset(size.width * 0.725, size.height * 0.46),
      glowRadius,
      Paint()..color = Colors.cyanAccent,
    );

    // --- Patas Fuertes y Estables ---
    final legWidth = size.width * 0.045;
    final legHeight = size.height * 0.12;
    
    canvas.drawRect(
      Rect.fromLTWH(size.width * 0.38, size.height * 0.75, legWidth, legHeight),
      paint,
    );
    canvas.drawRect(
      Rect.fromLTWH(size.width * 0.62, size.height * 0.75, legWidth, legHeight),
      paint,
    );

    // --- Espinas Dorsales (Estilo moderno) ---
    final spikePaint = Paint()..color = Colors.blue.shade900;
    for (double x = 0.38; x < 0.68; x += 0.08) {
      final pathSpike = Path();
      pathSpike.moveTo(size.width * x, size.height * 0.35);
      pathSpike.lineTo(size.width * (x - 0.03), size.height * 0.22);
      pathSpike.lineTo(size.width * (x + 0.03), size.height * 0.22);
      pathSpike.close();
      canvas.drawPath(pathSpike, spikePaint);
      // Añadimos borde blanco a las espinas para mantener el estilo
      canvas.drawPath(pathSpike, strokePaint);
    }

    // --- Efecto de Luz "Lux" (Glow) ---
    final glowPaint = Paint()
      ..color = Colors.cyan.withOpacity(0.4)
      ..maskFilter = const MaskFilter.blur(BlurStyle.normal, 12);
    canvas.drawCircle(
      Offset(size.width * 0.75, size.height * 0.40),
      size.width * 0.07,
      glowPaint,
    );
  }

  @override
  bool shouldRepaint(CustomPainter oldDelegate) => false;
}
