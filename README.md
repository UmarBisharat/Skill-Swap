# Campus Gig & SkillSwap Portal

A mobile marketplace where students offer skills, request help, and build reputation through mutual reviews. Built with Flutter during the AWS Hackathon (8:00 AM to 3:30 PM).

## Features

- **Role-flexible profiles**: every user can be a Poster or an Applicant. Profiles show major, skills, gigs posted, gigs completed and average rating.
- **Gig creation**: Offering or Requesting, with category, payment type (Paid / Skill Swap / Free), budget and deadline.
- **Discovery**: keyword search, plus filters for category, type, payment type and budget range.
- **Applications**: apply with a short message and track your application status. Applying to your own gig or applying twice is blocked.
- **Applicant selection**: owners accept one applicant. The gig moves to In Progress and all other pending applications are rejected automatically.
- **Status flow**: Open → In Progress → Completed. Open gigs past their deadline show as Expired.
- **Mutual reviews**: after completion, the owner and the accepted applicant each rate the other (1 to 5) once. Average ratings are calculated from stored reviews.
- **Animated UI**: floating blobs, staggered list animations, press-bounce cards, pulsing action button, loading skeletons and page transitions.

## Tech Stack

| Layer | Choice |
|---|---|
| Framework | Flutter (Dart) |
| State management | Provider |
| Local storage | Hive |
| Backend | REST-style mock API (`MockApi`), stored in Hive |

## Project Structure

```
lib/
├── main.dart
├── core/        constants, theme, utils
├── data/
│   ├── mock_api.dart      REST-style endpoints and all business rules
│   ├── seed.dart          sample data
│   └── models/            user, gig, application, review
├── providers/   app_state.dart
├── widgets/     common animations, gig card
└── screens/     splash, home, gig detail, create gig, activity, profile
```

## Mock API

All screens fetch and change data only through `MockApi`.

| Endpoint | Purpose |
|---|---|
| `GET /gigs?category=&type=&payment=&minBudget=&maxBudget=&q=` | Browse, filter and search gigs |
| `POST /gigs` | Create a gig (validated) |
| `PATCH /gigs/:id` | Owner changes status |
| `DELETE /gigs/:id` | Owner deletes a gig |
| `GET /applications` | List applications |
| `POST /applications` | Apply to a gig |
| `PATCH /applications/:id` | Accept or reject an applicant |
| `POST /reviews` | Leave a review |
| `GET /profile/:id` | Profile with calculated stats |

## Seed Data

12 users, 25 gigs, 20 applications and 8 reviews, covering Programming, Design, Writing and Tutoring, both gig types, and every status.

## Getting Started

```bash
git clone https://github.com/UmarBisharat/Skill-Swap.git
cd Skill-Swap
flutter pub get
flutter run
```

To reset the data, uninstall the app or clear its storage. The seed runs again on the next launch.

## Demo Flow

1. Open **Profile** → **Switch demo user** to act as different students.
2. As the gig owner, open a gig with applications and tap **Accept**.
3. Tap **Mark as completed**, then **Leave a review**.
4. Switch to the accepted applicant and leave the second review.
5. Check both profiles: ratings update automatically.

## Team

- @TeammateName1
- @TeammateName2
- @TeammateName3
- Umar Bisharat

## Future Work

- Replace the Hive-based mock with a real HTTP backend (MockAPI.io or AWS)
- User authentication
- Notifications for new applications and status changes
