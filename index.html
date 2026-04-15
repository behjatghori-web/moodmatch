'use client';
import { useState, useCallback, useRef } from 'react';

type Vendor = {
  rank: number;
  vendor: string;
  match_score: number;
  total_products: number;
  target_l2_count: number;
  brand_matches: number;
  y2k_brand_hits: number;
  keyword_hits: number;
  matched_brands: string;
};

type BuyerHistoryVendor = {
  rank: number;
  vendor: string;
  order_count: number;
  last_ordered_at: string | null;
  total_spend_gbp: number | null;
};

type StyleAnalysis = {
  aesthetic_summary: string;
  aesthetics: string[];
  l1: string;
  l2_targets: string[];
  style_keywords: string[];
  era_keywords: string[];
  priority_brands: string[];
  silhouette_notes: string;
  confidence: number | null;
};

type ApiResponse = {
  ok: boolean;
  style_analysis?: StyleAnalysis;
  vendors?: Vendor[];
  buyer_history_vendors?: BuyerHistoryVendor[];
  error?: string;
  generated_at?: string;
};

const VENDOR_COUNT_OPTIONS = [3, 5, 10, 15, 20] as const;

export default function Home() {
  const [images, setImages] = useState<string[]>([]);
  const [buyerName, setBuyerName] = useState('');
  const [buyerEmail, setBuyerEmail] = useState('');
  const [vendorsToReturn, setVendorsToReturn] = useState<number>(5);
  const [styleDescription, setStyleDescription] = useState('');
  const [loading, setLoading] = useState(false);
  const [result, setResult] = useState<ApiResponse | null>(null);
  const [error, setError] = useState<string | null>(null);
  const inputRef = useRef<HTMLInputElement>(null);
  const resultsRef = useRef<HTMLDivElement>(null);

  const onFiles = useCallback(async (files: FileList | null) => {
    if (!files) return;
    const reads = Array.from(files)
      .filter((f) => f.type.startsWith('image/'))
      .slice(0, 8)
      .map(
        (f) =>
          new Promise<string>((resolve, reject) => {
            const r = new FileReader();
            r.onload = () => resolve(r.result as string);
            r.onerror = reject;
            r.readAsDataURL(f);
          })
      );
    const urls = await Promise.all(reads);
    setImages((prev) => [...prev, ...urls].slice(0, 8));
  }, []);

  const submit = async () => {
    if (images.length === 0) return;
    setLoading(true);
    setError(null);
    setResult(null);
    try {
      const res = await fetch('/api/moodmatch', {
        method: 'POST',
        headers: { 'content-type': 'application/json' },
        body: JSON.stringify({
          images,
          brief: styleDescription.trim() || undefined,
          buyer_name: buyerName.trim() || undefined,
          buyer_email: buyerEmail.trim() || undefined,
          vendors_to_return: vendorsToReturn
        })
      });
      const data: ApiResponse = await res.json();
      if (!res.ok || !data.ok) throw new Error(data.error || `HTTP ${res.status}`);
      setResult(data);
      setTimeout(() => resultsRef.current?.scrollIntoView({ behavior: 'smooth' }), 150);
    } catch (e: any) {
      setError(e.message || 'Something went wrong');
    } finally {
      setLoading(false);
    }
  };

  const reset = () => {
    setImages([]);
    setBuyerName('');
    setBuyerEmail('');
    setStyleDescription('');
    setVendorsToReturn(5);
    setResult(null);
    setError(null);
  };

  return (
    <main className="min-h-screen">
      {/* ───────────── Header ───────────── */}
      <header className="sticky top-0 z-10 backdrop-blur-md bg-white/80 border-b border-gray-100">
        <div className="max-w-6xl mx-auto px-6 py-4 flex items-center justify-between">
          <div className="flex items-center gap-2 font-semibold text-lg">
            <span className="text-pink-hot">✦</span>
            <span className="text-ink">Mood</span>
            <span className="gradient-text">Match</span>
          </div>
          <div className="chip">by Fleek</div>
        </div>
      </header>

      {/* ───────────── Hero ───────────── */}
      <section className="relative bg-hero-gradient py-20 md:py-28 overflow-hidden">
        <div className="sparkle-bg absolute inset-0" />
        <div className="relative max-w-4xl mx-auto px-6 text-center">
          <div className="text-pink-hot text-xl mb-3 tracking-[0.4em]">✦ ✦ ✦</div>
          <h1 className="font-display text-5xl md:text-7xl leading-[1.05] tracking-tight text-ink">
            Find your <span className="gradient-text italic">perfect vendors!</span>
          </h1>
          <p className="mt-6 text-lg md:text-xl text-gray-600">
            Mood Match is your new Y2K bestie <span className="text-pink-rose">:)</span>
          </p>
          <p className="mt-2 text-base md:text-lg text-gray-500 max-w-2xl mx-auto">
            Upload a moodboard or paste image links — get matched vendors from the Fleek
            Womenswear catalog instantly.
          </p>
        </div>
      </section>

      {/* ───────────── Form ───────────── */}
      <section className="max-w-4xl mx-auto px-6 -mt-12 relative z-[1] pb-24 space-y-6">
        {/* Moodboard card */}
        <div className="card">
          <div className="section-label mb-4">Your moodboard</div>

          <div
            onDragOver={(e) => e.preventDefault()}
            onDrop={(e) => {
              e.preventDefault();
              onFiles(e.dataTransfer.files);
            }}
            onClick={() => inputRef.current?.click()}
            className="cursor-pointer border-2 border-dashed border-pink-rose/60 rounded-2xl p-10 md:p-14 text-center bg-pink-pale hover:bg-pink-cotton/40 transition"
          >
            <div className="text-5xl mb-4">🖼️</div>
            <div className="text-lg md:text-xl font-semibold text-pink-hot mb-1">
              Drop images here or click to upload
            </div>
            <div className="text-sm text-gray-500">JPG, PNG, WEBP — up to 8 images</div>
            <input
              ref={inputRef}
              type="file"
              accept="image/*"
              multiple
              hidden
              onChange={(e) => onFiles(e.target.files)}
            />
          </div>

          {images.length > 0 && (
            <div className="grid grid-cols-4 md:grid-cols-8 gap-3 mt-5">
              {images.map((src, i) => (
                <div
                  key={i}
                  className="relative aspect-square rounded-xl overflow-hidden border border-pink-cotton shadow-card"
                >
                  {/* eslint-disable-next-line @next/next/no-img-element */}
                  <img src={src} alt="" className="w-full h-full object-cover" />
                  <button
                    onClick={() => setImages((p) => p.filter((_, idx) => idx !== i))}
                    className="absolute top-1 right-1 w-6 h-6 bg-white/90 text-pink-hot rounded-full text-sm font-bold shadow hover:bg-white"
                    aria-label="Remove"
                  >
                    ×
                  </button>
                </div>
              ))}
            </div>
          )}
        </div>

        {/* Details card */}
        <div className="card">
          <div className="section-label mb-5">Details</div>

          <div className="grid md:grid-cols-2 gap-5">
            <div>
              <label className="field-label">Buyer Name</label>
              <input
                type="text"
                className="field-input"
                placeholder="e.g. Sarah from NYC"
                value={buyerName}
                onChange={(e) => setBuyerName(e.target.value)}
              />
            </div>

            <div>
              <label className="field-label">Vendors to return</label>
              <select
                className="field-input appearance-none pr-10 bg-no-repeat bg-[length:1rem_1rem] bg-[right_1rem_center]"
                style={{
                  backgroundImage:
                    "url(\"data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 20 20' fill='%23ff5ca7'><path d='M5.25 7.5l4.75 5 4.75-5z'/></svg>\")"
                }}
                value={vendorsToReturn}
                onChange={(e) => setVendorsToReturn(Number(e.target.value))}
              >
                {VENDOR_COUNT_OPTIONS.map((n) => (
                  <option key={n} value={n}>
                    Top {n}
                  </option>
                ))}
              </select>
            </div>

            <div className="md:col-span-2">
              <label className="field-label">
                Buyer Email <span className="text-gray-400 font-normal">(optional — pulls their previous vendors)</span>
              </label>
              <input
                type="email"
                className="field-input"
                placeholder="buyer@brand.com"
                value={buyerEmail}
                onChange={(e) => setBuyerEmail(e.target.value)}
              />
            </div>

            <div className="md:col-span-2">
              <label className="field-label">
                Style Description <span className="text-gray-400 font-normal">(optional)</span>
              </label>
              <textarea
                className="field-input resize-none"
                rows={3}
                placeholder="e.g. Y2K glam, velour tracksuits, Juicy Couture vibes, 2000s mall girl..."
                value={styleDescription}
                onChange={(e) => setStyleDescription(e.target.value)}
              />
            </div>
          </div>
        </div>

        {/* CTA */}
        <div className="flex flex-col md:flex-row items-center gap-4 justify-center pt-2">
          <button
            className="cta-button"
            onClick={submit}
            disabled={loading || images.length === 0}
          >
            {loading ? (
              <>
                <span className="inline-block animate-pulse">✦</span>
                Finding your vendors...
              </>
            ) : (
              <>
                <span>✦</span>
                Find my vendors
              </>
            )}
          </button>
          {(images.length > 0 || buyerName || buyerEmail || styleDescription) && !loading && (
            <button className="text-sm text-gray-500 hover:text-pink-hot underline" onClick={reset}>
              reset
            </button>
          )}
        </div>

        {error && (
          <div className="card border-pink-hot/40 bg-pink-pale">
            <div className="text-pink-hot font-semibold mb-1">✗ Error</div>
            <div className="text-sm text-ink">{error}</div>
          </div>
        )}

        {/* ───────────── Results ───────────── */}
        {result?.ok && (
          <div ref={resultsRef} className="space-y-6 pt-4">
            {/* Style read */}
            {result.style_analysis && (
              <div className="card bg-gradient-to-br from-pink-pale via-white to-sky-pale">
                <div className="section-label mb-3">Style read</div>
                <p className="text-lg text-ink mb-4">
                  {result.style_analysis.aesthetic_summary}
                </p>
                <div className="flex flex-wrap gap-2 mb-5">
                  {result.style_analysis.aesthetics.map((a) => (
                    <span key={a} className="chip">
                      {a}
                    </span>
                  ))}
                </div>
                <div className="grid md:grid-cols-2 gap-4 text-sm">
                  <div>
                    <div className="font-semibold text-ink mb-1">Category</div>
                    <div className="text-gray-600">
                      {result.style_analysis.l1}
                      {result.style_analysis.l2_targets.length > 0 && (
                        <> → {result.style_analysis.l2_targets.join(', ')}</>
                      )}
                    </div>
                  </div>
                  <div>
                    <div className="font-semibold text-ink mb-1">Priority brands</div>
                    <div className="text-gray-600">
                      {result.style_analysis.priority_brands.join(', ') || '—'}
                    </div>
                  </div>
                  <div>
                    <div className="font-semibold text-ink mb-1">Style keywords</div>
                    <div className="text-gray-600">
                      {result.style_analysis.style_keywords.join(', ')}
                    </div>
                  </div>
                  <div>
                    <div className="font-semibold text-ink mb-1">Silhouettes</div>
                    <div className="text-gray-600">{result.style_analysis.silhouette_notes}</div>
                  </div>
                </div>
              </div>
            )}

            {/* PRIMARY: moodboard-matched vendors */}
            {result.vendors && result.vendors.length > 0 && (
              <div>
                <div className="flex items-baseline justify-between mb-4 px-1">
                  <h2 className="font-display text-3xl md:text-4xl text-ink">
                    <span className="gradient-text">Moodboard matches</span>
                  </h2>
                  <span className="text-sm text-gray-500">Ranked by brand + style DNA</span>
                </div>
                <div className="space-y-3">
                  {result.vendors.map((v) => (
                    <div key={v.vendor} className="card flex items-center gap-5 py-5">
                      <div className="font-display text-4xl md:text-5xl gradient-text w-14 text-center">
                        {v.rank}
                      </div>
                      <div className="flex-1 min-w-0">
                        <div className="flex items-baseline gap-3 flex-wrap">
                          <a
                            href={`https://joinfleek.com/vendors/${v.vendor}`}
                            target="_blank"
                            rel="noreferrer"
                            className="font-semibold text-lg text-ink hover:text-pink-hot underline decoration-pink-cotton decoration-2 underline-offset-4"
                          >
                            {v.vendor}
                          </a>
                          <span className="chip">{v.match_score} pts</span>
                        </div>
                        <div className="mt-1 text-sm text-gray-500">
                          {v.total_products.toLocaleString()} products · {v.target_l2_count} in
                          target · {v.brand_matches} brand matches · {v.y2k_brand_hits} Y2K · {v.keyword_hits} keyword hits
                        </div>
                        {v.matched_brands && (
                          <div className="mt-1 text-sm text-ink">
                            <span className="font-semibold">Brands: </span>
                            <span className="text-gray-700">{v.matched_brands}</span>
                          </div>
                        )}
                      </div>
                    </div>
                  ))}
                </div>
              </div>
            )}

            {/* SECONDARY: buyer-history vendors */}
            {result.buyer_history_vendors && result.buyer_history_vendors.length > 0 && (
              <div>
                <div className="flex items-baseline justify-between mb-4 px-1 mt-10">
                  <h2 className="font-display text-3xl md:text-4xl text-ink">
                    <span className="gradient-text italic">Previously loved</span>
                  </h2>
                  <span className="text-sm text-gray-500">
                    {buyerName ? `${buyerName}'s` : 'Buyer\u2019s'} top-used vendors
                  </span>
                </div>
                <div className="grid md:grid-cols-3 gap-4">
                  {result.buyer_history_vendors.map((v) => (
                    <div key={v.vendor} className="card py-5">
                      <div className="flex items-baseline gap-2 mb-2">
                        <span className="font-display text-3xl gradient-text">#{v.rank}</span>
                        <a
                          href={`https://joinfleek.com/vendors/${v.vendor}`}
                          target="_blank"
                          rel="noreferrer"
                          className="font-semibold text-ink hover:text-pink-hot underline decoration-pink-cotton decoration-2 underline-offset-4"
                        >
                          {v.vendor}
                        </a>
                      </div>
                      <div className="text-sm text-gray-600">
                        <div>
                          <span className="font-semibold text-ink">{v.order_count}</span>{' '}
                          {v.order_count === 1 ? 'order' : 'orders'}
                        </div>
                        {v.last_ordered_at && (
                          <div>
                            Last:{' '}
                            {new Date(v.last_ordered_at).toLocaleDateString('en-GB', {
                              month: 'short',
                              year: 'numeric'
                            })}
                          </div>
                        )}
                        {typeof v.total_spend_gbp === 'number' && v.total_spend_gbp > 0 && (
                          <div>Spend: £{Math.round(v.total_spend_gbp).toLocaleString()}</div>
                        )}
                      </div>
                    </div>
                  ))}
                </div>
              </div>
            )}

            {/* Empty state if email was provided but no history found */}
            {buyerEmail &&
              (!result.buyer_history_vendors || result.buyer_history_vendors.length === 0) && (
                <div className="card bg-mist border-dashed text-center text-gray-500 text-sm">
                  No previous order history found for <span className="font-mono">{buyerEmail}</span>.
                </div>
              )}
          </div>
        )}
      </section>

      <footer className="border-t border-gray-100 py-8 text-center text-xs text-gray-400">
        Mood Match · a Fleek internal tool · {new Date().getFullYear()}
      </footer>
    </main>
  );
}
