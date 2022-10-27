<script setup lang="ts">
import * as _plantumlencoder from 'plantuml-encoder'

const code = `
@startuml

skinparam linetype ortho

enum StreamingPlatformEnum {
  Offline
  AmazonVideo
  Netflix
  Sky
  DisneyPlus
  GooglePlay
  AppleTV
  ZdfMediathek
  ArdMediathek
}

enum DynamicEnum {
  Connect
  Break
  Quiet
  Medium
  Loud
}

enum HarmonyEnum {
  C
  CSharpDFlat
  D
  DSharpEFlat
  E
  F
  FSharpGFlat
  G
  GSharpAFlat
  A
  ASharpBFlat
  B
}

enum TonalityEnum {
  Tonal
  Atonal
  Soundbased
}

enum HarmonicStructureEnum {
  SingleNoteOrUnison
  SingleIntervalOrInTwoVoices
  SingleChord
  ModalHarmony
  FunctionalHarmony
  ExtendedHarmony
  Other
  No
}

enum FunctionEnum {
  Psychologizing
  Illustrative
  Transgressive
  Other
}

enum ScaleEnum {
  Major
  MelodicOrHarmonicMinor
  Aeolian
  Dorian
  Phrygian
  Lydian
  Mixolydian
  BluesScale
  Pentatonic
  WholeTone
  WhTHTOrHTWhT
  Other
}

enum PksEnum {
  StereotypeLed
  ConceptLed
  MotiveLed
}

enum EffectEnum {
  Percussive
  Glissando
  Contemporary
  Electronic
  Sound
  Microtonal
  No
}

enum ClusterEnum {
  WholeTone
  Diatonic
  Chromatic
  Microtonal
  No
}

enum KindEnum {
  Diegetic
  Transgressive
  NonDiegetic
}

enum OrchestrationTypeEnum {
  MelodyOrLeitmotif
  OstinatoOrRepetitivePattern
  Sustained
  Other
}

entity User {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  oidcAccessToken: String?
  * email: String
  * firstName: String
  midName: String?
  lastName: String?
  work: String?
  * movie: Movie[]
  * timeline: Timeline[]
}

entity Movie {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  * tmdbId: Int
  * imdbId: String
  * createdBy_id: String
  * createdBy: User
  * title: String
  * genre: Genre[]
  * year: Int
  imgUrl: String?
  * timeline: Timeline[]
}

entity Genre {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  * tmdbId: Int
  * name: String
  * movie: Movie[]
}

entity Keyword {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  * name: String
  * timelineKeyword: TimelineKeyword[]
}

entity Instrument {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  * name: String
  * timelineOrchestration: TimelineOrchestration[]
}

entity Timeline {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  * author_id: String
  author: User?
  * movie_id: String
  * movie: Movie
  * length: Int
  * source: StreamingPlatformEnum
  * descriptionShort: String
  descriptionLong: String?
  * completed: Boolean
  * dirty: Boolean
  * timelineBpm: TimelineBpm[]
  * timelineTimeSignature: TimelineTimeSignature[]
  * timelineTranscription: TimelineTranscription[]
  * timelineDynamic: TimelineDynamic[]
  * timelineTonality: TimelineTonality[]
  * timelineFunction: TimelineFunction[]
  * timelineHarmonicStructure: TimelineHarmonicStructure[]
  * timelineRoot: TimelineRoot[]
  * timelineScale: TimelineScale[]
  * timelineComment: TimelineComment[]
  * timelinePks: TimelinePks[]
  * timelineEffect: TimelineEffect[]
  * timelineCluster: TimelineCluster[]
  * timelineKind: TimelineKind[]
  * timelineKeyword: TimelineKeyword[]
  * timelineOrchestration: TimelineOrchestration[]
}

entity TimelineBpm {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  * start: Int
  * end: Int
  * timelineId: String
  * timeline: Timeline
  error: String?
  bpm: Int?
  * connect: Boolean
}

entity TimelineComment {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  * start: Int
  * end: Int
  * timelineId: String
  * timeline: Timeline
  error: String?
  * comment: String
}

entity TimelineTimeSignature {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  * start: Int
  * end: Int
  * timelineId: String
  * timeline: Timeline
  error: String?
  timeSignature: String?
}

entity TimelineTranscription {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  * start: Int
  * end: Int
  * timelineId: String
  * timeline: Timeline
  error: String?
  * transcription: String
}

entity TimelineDynamic {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  * start: Int
  * end: Int
  * timelineId: String
  * timeline: Timeline
  error: String?
  * dynamic: DynamicEnum
}

entity TimelineTonality {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  * start: Int
  * end: Int
  * timelineId: String
  * timeline: Timeline
  error: String?
  * tonality: TonalityEnum
}

entity TimelineFunction {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  * start: Int
  * end: Int
  * timelineId: String
  * timeline: Timeline
  error: String?
  * function: FunctionEnum
}

entity TimelineHarmonicStructure {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  * start: Int
  * end: Int
  * timelineId: String
  * timeline: Timeline
  error: String?
  * harmonicStructure: HarmonicStructureEnum
}

entity TimelineRoot {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  * start: Int
  * end: Int
  * timelineId: String
  * timeline: Timeline
  error: String?
  root: HarmonyEnum?
}

entity TimelineScale {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  * start: Int
  * end: Int
  * timelineId: String
  * timeline: Timeline
  error: String?
  * scale: ScaleEnum
}

entity TimelinePks {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  * start: Int
  * end: Int
  * timelineId: String
  * timeline: Timeline
  error: String?
  * pks: PksEnum
}

entity TimelineEffect {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  * start: Int
  * end: Int
  * timelineId: String
  * timeline: Timeline
  error: String?
  effect: EffectEnum?
}

entity TimelineCluster {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  * start: Int
  * end: Int
  * timelineId: String
  * timeline: Timeline
  error: String?
  cluster: ClusterEnum?
}

entity TimelineKind {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  * start: Int
  * end: Int
  * timelineId: String
  * timeline: Timeline
  error: String?
  * kind: KindEnum
}

entity TimelineKeyword {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  * start: Int
  * end: Int
  * timelineId: String
  * timeline: Timeline
  error: String?
  * keywordId: String
  * keyword: Keyword
}

entity TimelineOrchestration {
  * id: String
  * createdAt: DateTime
  * updatedAt: DateTime
  * start: Int
  * end: Int
  * timelineId: String
  * timeline: Timeline
  error: String?
  * instrumentId: String
  * instrument: Instrument
  type: OrchestrationTypeEnum?
}

User ||..|{ Movie
User ||..|{ Movie
Movie }|..|{ Genre
Keyword ||..|{ TimelineKeyword
Instrument ||..|{ TimelineOrchestration
User |o..|{ Timeline
Timeline ||..|{ TimelineBpm
Timeline ||..|{ TimelineComment
Timeline ||..|{ TimelineTimeSignature
Timeline ||..|{ TimelineTranscription
Timeline ||..|{ TimelineDynamic
Timeline ||..|{ TimelineTonality
Timeline ||..|{ TimelineFunction
Timeline ||..|{ TimelineHarmonicStructure
Timeline ||..|{ TimelineRoot
Timeline ||..|{ TimelineScale
Timeline ||..|{ TimelinePks
Timeline ||..|{ TimelineEffect
Timeline ||..|{ TimelineCluster
Timeline ||..|{ TimelineKind
Keyword ||..|{ TimelineKeyword
Instrument ||..|{ TimelineOrchestration
Timeline ||..|| StreamingPlatformEnum
TimelineDynamic ||..|| DynamicEnum
TimelineRoot ||..o| HarmonyEnum
TimelineTonality ||..|| TonalityEnum
TimelineHarmonicStructure ||..|| HarmonicStructureEnum
TimelineFunction ||..|| FunctionEnum
TimelineScale ||..|| ScaleEnum
TimelinePks ||..|| PksEnum
TimelineEffect ||..o| EffectEnum
TimelineCluster ||..o| ClusterEnum
TimelineKind ||..|| KindEnum
TimelineOrchestration ||..o| OrchestrationTypeEnum

@enduml`

const codePrepared = _plantumlencoder.encode.call(void 0, code.trim())
</script>

<template>
  <PlantUml
    :code="codePrepared"
    :server="$slidev.configs.plantUmlServer"
    :scale="1" />
</template>
